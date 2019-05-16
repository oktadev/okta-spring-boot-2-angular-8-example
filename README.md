# Angular 8 + Spring Boot 2.2 = ❤️
 
This example app shows how to build a basic CRUD app with Spring Boot 2.2, Spring Data, Angular 8, and Angular Material.

Please read [Angular 8 + Spring Boot 2.2: Build a CRUD App Today!](https://developer.okta.com/blog/2019/05/13/angular-8-spring-boot-2) to see how this app was created.

**Prerequisites:** [Java 11](https://sdkman.io/sdks#java) and [Node.js](https://nodejs.org/). 

> [Okta](https://developer.okta.com/) has Authentication and User Management APIs that reduce development time with instant-on, scalable user infrastructure. Okta's intuitive API and expert support make it easy for developers to authenticate, manage and secure users and roles in any application.

* [Getting Started](#getting-started)
* [Links](#links)
* [Help](#help)
* [License](#license)

## Getting Started

To install this example application, run the following commands:

```bash
git clone https://github.com/oktadeveloper/okta-spring-boot-2-angular-8-example.git
cd okta-spring-boot-2-angular-8-example
```

This will get a copy of the project installed locally. To install all of its dependencies and start each app, follow the instructions below.

To run the server, cd into the `server` folder and run:
 
```bash
./mvnw spring-boot:run
```

To run the client, cd into the `client` folder and run:
 
```bash
npm install && npm start
```

### Create a New OIDC App in Okta

If you don't have an Okta developer account, please [create one](https://developer.okta.com/signup/). Then, create a new OIDC app on Okta:

1. Log in to your developer account, navigate to **Applications** > **Add Application**.
3. Select **Single-Page App** > **Next**. 
4. Give the application a name, change all instances of `https://localhost:8080` to `https://localhost:4200`, and click **Done**.

#### Server Configuration

Set your domain and copy the `clientId` into `server/src/main/resources/application.properties`. 

**NOTE:** The value of `{yourOktaDomain}` should be something like `dev-123456.okta.com`. Make sure you don't include `-admin` in the value!

```properties
okta.oauth2.client-id: {clientId}
okta.oauth2.issuer: https://{yourOktaDomain}/oauth2/default
```

#### Client Configuration

For the client, set the `issuer` and copy the `clientId` into `client/src/app/auth-routing.module.ts`.

```typescript
const config = {
  issuer: 'https://{yourOktaDomain}/oauth2/default',
  redirectUri: window.location.origin + '/implicit/callback',
  clientId: '{clientId}'
};
```

## Links

This example uses the following open source libraries from Okta:

* [Okta Spring Boot Starter](https://github.com/okta/okta-spring-boot#readme)
* [Okta Angular SDK](https://github.com/okta/okta-oidc-js/tree/master/packages/okta-angular#readme)
* [OktaDev Schematics](https://github.com/oktadeveloper/schematics#readme)

## Help

Please post any questions as commnets on the [blog post](https://developer.okta.com/blog/2019/05/13/angular-8-spring-boot-2) or ask them on the [Okta Developer Forums](https://devforum.okta.com/). Our whole team monitors this channel and will see your questions. You can also enter them as issues on this project or ask them on Stack Overflow and add the `okta` tag.

## License

Apache 2.0, see [LICENSE](LICENSE).
