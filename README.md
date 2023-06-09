# developer-assignment

Please return the assignment as a private Github repo with access given to Github account(s) provided to you by us.

## Overview

At Noice many of our systems rely on event-based (pub/sub) communication. An example of such system is chat. Chat can take many forms from lobby chats with thousands of users to one-to-one chats between users. In this assignment we will only focus on the former where all users can chat together in a single room ("lobby").

### Example chat message struct

Chat messages should contain at least the information described in the struct below

```
ChatMessage {
    from_user: string
    sent_at: time
    text: string
}
```

## Assignments

There are three different types of assigments:

- [Backend](#Backend)
- [Frontend](#Frontend)
- [Fullstack](#Fullstack)

 You only need to implement one of them depending on which type of role you are applying for.

### Backend

Build a chat backend in which users can join the *lobby chat*, receive list of existing users, get updates on users joining or leaving, receive messages, send messages and leave the chat.

#### Requirements

- Use Golang
- Service should be horizontally scalable and it needs to be runnable on multiple instances with different users connecting to different processes (tip: you can for example use something like Nats or Redis for the service to service communication)
- Expose an interface usable from a modern browser where clients can receive real time updates (these could be WebSockets, REST or if you are feeling wild even WebTransport). Your API must support streaming for receiving messages and updates.
- Easy to run two instances of the server and all its dependencies (tip: docker-compose)
- Doesn't need to be production-ready but please follow standard quality practices (code structure, testing)

#### Nice to have

- Gracefully shutdown the service
- Expose metrics by using instrumentation for Prometheus (just the metrics endpoint, no need to setup Prometheus itself)

### Frontend

Build a chat lobby frontend where users can join with a specific username, send and receive messages, and see "user joining" and "user leaving" updates. Mock the server calls and implement only the frontend.

- Login view
    - Input for choosing your username (preferably with validation of username being > 3 characters)
    - Join room button
- Chat lobby view
    - Feel free to use [WhatsApp](https://www.whatsapp.com/) or [Discord](https://discord.com/) as inspiration
    - Messages should preferrably start from the bottom of the view and move up as more messages are added, and should include sender information (such as username), message, and time sent (tip: look at the flexbox API for an easy way to accomplish this)
    - Clicking on a user should open up a basic profile view for them
    - If you are feeling really crazy feel free to add a basic/limited emoji picker :D
- User profile view
    - Limited user profile view with basic but relevant information, such as:
        - Online status
        - When the user joined/was last seen
        - If you can infer any other information to use for the user, go for it!

#### Requirements
- Use React
- Utilize React hooks to manage logic
- Using [TypeScript](https://create-react-app.dev/docs/adding-typescript/) is preferred
- Styling with [CSS modules](https://create-react-app.dev/docs/adding-a-css-modules-stylesheet/) is preferred
- Easy to run using [yarn](https://yarnpkg.com/)
- Feel free to use a boilerplate app generation tool like [Create React App](https://github.com/facebook/create-react-app) to get started
- If you use any additional libraries, please explain why
- Doesn't need to be production-ready, but please follow standard quality practices
- If you feel inspired check out the [Fullstack](#Fullstack) assigment but not a requirement ;)

### Fullstack

Implement a single instance version (no need for the multi server part) of the [Backend](#Backend) in language of your choosing (for more backend focus prefer Golang) and the [Frontend](#Frontend).
