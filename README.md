# Svelte Hipster

[![NPM version][npm-image]][npm-url] [![Dependency Status][daviddm-image]][daviddm-url] [![code style: prettier][prettier-image]][prettier-url] [![Generated applications build status][github-actions-apps-generator-dev-image]][github-actions-url] [![Generated applications build status][github-actions-apps-generator-prod-image]][github-actions-url] [![Generator Build Status][github-actions-generator-image]][github-actions-url]

> Generate cybernetically enhanced JHipster Svelte web applications

## Introduction

This is a [JHipster](https://www.jhipster.tech/) blueprint, that intends to use [SvelteKit](https://kit.svelte.dev/) / [Svelte](https://svelte.dev/) as the client side development framework.

## What's new

Refer to the [changelog](./CHANGELOG.md) to gain more insights into each release details.

## Supported flows and integrations

> Under active development

Following integrations are supported:

    ✅ Session, JWT, OIDC authentication
    ✅ Dark Mode support
    ✅ SvelteKit, Vite integration
    ✅ Tailwind CSS
    ✅ Prettier, EsLint integration
    ✅ Cypress integration for end to end tests
    ✅ Jest and Testing Library integration for unit tests
    ✅ JHipster application JDL
    ✅ JHipster entity JDL (simple data type, no relation)
    ✅ JHipster elasticsearch integration

Following functional flows are covered with end to end tests:

    ✅ Sign in
    ✅ Sign up
    ✅ Forgot Password
    ✅ Home
    ✅ Account
        ✅ Change Password
        ✅ Settings
        ✅ Sign out
    ✅ Administration
        ✅ User Management (List, Create, Update, View, Delete)
        ✅ Loggers
    ✅ Entities
        ✅ Entity (List, View, Delete, Search, Pagination)

For more details, you can check out the source code of [sample application](https://github.com/jhipster/jhipster-sample-app-svelte)

## Technical Stack

<a href="https://svelte.dev" target="_blank" ><img alt="Svelte JS" height="50px" src="https://svelte.dev/svelte-logo-horizontal.svg"></a>
<a href="https://tailwindcss.com/" target="_blank" ><img alt="Tailwind CSS" height="50px" src="https://refactoringui.nyc3.cdn.digitaloceanspaces.com/tailwind-logo.svg"></a>
<a href="https://fontawesome.com/" target="_blank"><img alt="Font Awesome" height="50px" src="https://api.iconify.design/simple-icons:fontawesome.svg"></a>
<a href="https://www.cypress.io/" target="_blank" style="display:inline-block;" ><img alt="Cypress" height="50px" src="https://cloud.githubusercontent.com/assets/1268976/20607953/d7ae489c-b24a-11e6-9cc4-91c6c74c5e88.png"></a>
<a href="https://jestjs.io/" target="_blank" ><img alt="Jest" height="50px" src="https://api.iconify.design/logos:jest.svg"></a>
<a href="https://testing-library.com/" target="_blank"><img alt="Testing Library" height="50px" src="https://testing-library.com/img/octopus-128x128.png"></a>
<a href="https://prettier.io/" target="_blank"><img alt="Prettier" height="50px" src="https://raw.githubusercontent.com/prettier/prettier-logo/master/images/prettier-banner-dark.png"></a>
<a href="https://prettier.io/" target="_blank"><img alt="ESLint" height="50px" src="https://api.iconify.design/logos:eslint.svg"></a>
<a href="https://vitejs.dev/guide/" target="_blank"><img alt="Vite" height="50px" src="https://vitejs.dev/logo.svg"></a>

## Installation

To install the blueprint, run below command:

```bash
npm install -g generator-jhipster-svelte
```

To update the blueprint, run below command:

```bash
npm update -g generator-jhipster-svelte
```

## Usage

-   Svelte Hipster blueprint exposes a `cli` to use the correct version of `JHipster`. Run the below command to generate new applications (`interactive` approach):

    ```bash
    shipster
    ```

-   Alternatively, you can also use the application `JDL` to generate new applications (`config` approach). Refer to [JDL application](https://www.jhipster.tech/jdl/applications) documentation for all supported options.

    Create a new application JDL like below and save it in a file (`app.jdl` in this example):

    ```
    application {
        config {
            baseName SampleBlogApp,
            applicationType monolith,
            authenticationType session,
            packageName tech.jhipster.samples.blog,
            prodDatabaseType postgresql,
            cacheProvider caffeine,
            buildTool maven
        }
        entities *
    }

    entity Blog {
        name String required minlength(3)
        handle String required minlength(2)
    }

    entity Tag {
        name String required minlength(3)
    }

    paginate Tag with pagination
    ```

    Pass `import-jdl` option along the file path to `shipster` cli to generate new application:

    ```bash
    shipster import-jdl app.jdl
    ```

-   If you have already setup [JHipster](https://www.jhipster.tech/installation/) on your workstation, then, run the below command (it overrides to use the global `JHipster` version). Be cautious to use compatible `Svelte Hipster` and `JHipster` versions.

    ```bash
    jhipster --blueprints svelte
    ```

## JHipster Compatibility Matrix

| `JHipster` | `Svelte Hipster` |
| ---------- | ---------------- |
| `6.10.5`   | `0.1` - `0.2.1`  |
| `7.0.x`    | `0.3` - `0.4`    |
| `7.1.x`    | >= `0.5`         |

## Docker development

Svelte Hipster docker images are available at [DockerHub](https://hub.docker.com/r/jhipster/svelte-hipster)

To develop against the latest published release, follow below steps:

-   Pull the `Svelte Hipster` docker image:

```sh
docker pull jhipster/svelte-hipster
```

In case, you want to try out the latest code (unpublished), then, pull the image with `main` tag as:

```sh
docker pull jhipster/svelte-hipster:main
```

-   Create a new directory for your application and run the below command to generate the application:

```sh
mkdir svelte-app && cd svelte-app

docker run -it --rm -v $PWD:/app jhipster/svelte-hipster
```

-   You can also run the generated application from within the container. Following examples consider `maven` as the build tool:

    -   To run unit test cases, use the command:

    ```sh
    docker run -it --rm -v $PWD:/app -v ~/.m2:/home/shipster/.m2 --entrypoint ./mvnw jhipster/svelte-hipster clean test
    ```

    -   To start the application using the default `dev` profile, use the command:

    ```sh
    docker run -it --rm -v $PWD:/app -v ~/.m2:/home/shipster/.m2 -p 8080:8080 --entrypoint ./mvnw jhipster/svelte-hipster -DskipTests
    ```

    Access application with http://localhost:8080/

-   If you would like to access the container file system, you can also attach a bourne shell:

```sh
docker run -it --rm -v $PWD:/app -v ~/.m2:/home/shipster/.m2 --entrypoint sh jhipster/svelte-hipster
```

## 🛠️ Local Development

> Pull requests are encouraged and always welcome.

To setup your development environment, follow below steps:

1. Link svelte blueprint globally:

```bash
cd generator-jhipster-svelte
npm link
```

2. Link a development version of JHipster to your blueprint (optional: required only if you want to use a non-released JHipster version, like the main branch or your own custom fork)

```bash
cd generator-jhipster
npm link

cd generator-jhipster-svelte
npm link generator-jhipster
```

3. Create a new directory for your application and link `JHipster` and `svelte` blueprint.

```bash
mkdir my-app && cd my-app

npm link generator-jhipster-svelte
npm link generator-jhipster (Optional: Needed only if you are using a non-released JHipster version)

shipster

```

## License

Apache-2.0 © [Vishal Mahajan](https://twitter.com/vishal423)

[npm-image]: https://img.shields.io/npm/v/generator-jhipster-svelte.svg
[npm-url]: https://npmjs.org/package/generator-jhipster-svelte
[daviddm-image]: https://david-dm.org/jhipster/generator-jhipster-svelte.svg?theme=shields.io
[daviddm-url]: https://david-dm.org/jhipster/generator-jhipster-svelte
[prettier-image]: https://img.shields.io/badge/code_style-prettier-ff69b4.svg?style=flat-square
[prettier-url]: https://github.com/prettier/prettier
[github-actions-apps-generator-dev-image]: https://github.com/jhipster/generator-jhipster-svelte/workflows/Svelte%20Dev%20Profile%20Applications/badge.svg
[github-actions-apps-generator-prod-image]: https://github.com/jhipster/generator-jhipster-svelte/workflows/Svelte%20Prod%20Profile%20Applications/badge.svg
[github-actions-generator-image]: https://github.com/jhipster/generator-jhipster-svelte/workflows/Svelte%20Generator/badge.svg
[github-actions-url]: https://github.com/jhipster/generator-jhipster-svelte/actions
