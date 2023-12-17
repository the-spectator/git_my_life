# Why do we really want to do?

Git based Journaling.

# Approach

1. Website

- Regular website, either a fullstack rails application or JS SPA as frontend and GO backend.
- Interact with Git hosting sites like Github via Oauth APIs. Use adapter system for Gitlab, Bitbucket.
- We have to store the hosting sites token in our database. So it won't be fully database free.
- Possible Learnings:
  - Interacting with github & other oauth APIs and handle ratelimits and other constraint.
  - Encryption.
  - Git as data store.
  - Hosting and maintaining a application on Ec2 or equivalent. Setup your own reverse proxy.
  - Have to store the encryption keys (partial encryption keys) in backend.
- Pros:
  - Everything is centralized
  - Easy to see the adoption and monitoring usage
- Cons:
  - Have to host it in some provider, costing money $$.
  - Low visiblity.
  - Not truly distributed.
  - Not really private as we the central hosting service can derive your data.

2. binary approach.

- package your application in single binary containing both front-end and backend.
- it would be available by brew or apt.
- We would directly manipulate the commits using libraries example: https://github.com/go-git/go-git or https://github.com/libgit2/rugged
- The encryption keys will be stored to locally to the user system.
- Don't have to use adapter system. Will piggy back on git push thing.
- Workflow envisioned.

  ```ruby
    brew install git_my_life
    git_my_life init # creates git directory and initial scaffold.
    git_my_life configure origin
    git_my_life start # starts http server that would serve frontend and frontend will communicate with api.

  ```

- Pros:
  - No hosting.
  - No headache of storing encryption keys.
- Cons:
  - Low visiblity
  - Hard to debug. Hard to integrate any error reporting service.
