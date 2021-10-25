## Cypress
Cypress is a JavaScript-based end-to-end testing framework that doesn't use Selenium. It is built on top of Mocha and runs in the browser simplifying asynchronous testing. Mocha is a testing framework for JavaScript and tests should be written using Mocha’s BDD interface. Cypress can be configured to use Cucumber as well.  Their website states that Cypress is fast, easy and reliable testing for anything that runs in a browser. Cypress was created to target the needs of front end developers and QA engineers to make it easy to write unit, integration and end to end tests.

![image](https://user-images.githubusercontent.com/10534266/138623669-ec52c739-4e00-4211-b4ed-4806b60447b3.png)

## Javascript-based
**Pro:** 
Cypress was built for developers and QA engineers with the intention of making it easy to test the UI. It can test anything that runs in a browser.  With Cypress, you have to write your tests using javascript. If you are a front-end developer or know javascript this is fantastic!  You can write tests in the same language as your code.

**Con:** 
Cypress doesn’t support any other language.  With Selenium, for instance, you can write your tests in any language. If you already have back-end operations with a different language, it may not make sense to use Cypress.  It also requires more **advanced javascript knowledge (promises, jquery) than webdriver-nodeJS frameworks**.  For instance, there is no async/await support so you’re stuck with promises. **Because it runs in the browser there is not support for multiple tabs**.

## Parallel Execution
**Pro:** 
Cypress can run recorded tests in parallel across multiple virtual machines since version 3.1.0.  You just pass in a  --parallel flag and spin up multiple machines on your CI provider and Cypress will automatically load balance all of your specs.

**Con:**
Parallel tests can technically run on a single machine, but Cypress does not recommend it since the machine would require significant resources to run your tests efficiently.  You will also need to manage and maintain the machines you spin up on your CI.  Beware of the pricing if taking this approach as it can get expensive to run multiple machines and some CI’s have a maximum number they will support.  (For a different approach, check out running your tests on Testery so you don’t have to manage or maintain your testing infrastructure.)

## CrossBrowser Testing
**Pro:**
Until Spring of 2020, Cypress only supported **Chrome**.  However, with a recent release, Cypress started supporting **Firefox and Edge** as well.  Now companies can do some cross browser testing with Cypress.  Chrome is the most popular browser so Cypress covers +70% of the market between Chrome, Firefox and Edge.  Here is a list of the current browsers Cypress supports.
**Con:**
Cypress doesn’t support any other browsers such as **IE, Safari, or Opera.** If you have a requirement ensuring that your web apps run smoothly across all browsers Cypress may not be a good option for you. Here’s a blog post where Testery talks about if cross browser testing is necessary.

## Mobile Testing
**Pro:**
Don’t need mobile testing? Perfect...because Cypress doesn’t support mobile testing.
**Con:**
Cypress doesn’t support mobile testing so you will need another testing solution if you have this requirement.

**Stability**
**Pro:**
Cypress has a built-in mechanism that handles waiting for **DOM elements** (there is a maximum waiting time setting that defaults to 10,000 ms). This means features like **sleep or wait are not necessary**.  It also eliminates a few selenium webdriver errors/exceptions caused by dynamic page content.  The result is more stable tests that run faster.  It also has built-in retries. Modern web applications are continually updating themselves, and they're a little unpredictable.  These all make Cypress less flaky.

**Con:**
A few things that developers are having to find hacks to deal with are: navigating to a URL command is flaky, no shadow DOM support, working with **iframes** is a huge pain, can’t work with **more than one tab**, and **can’t navigate to a different domain URL** (in case you want to test third party apps in your workflow).

## Native Event Handling
**Pro:** Cypress states that support for native event handling is on their roadmap.
**Con:** Cypress does not handle all native events as it uses synthetic events.  This makes it difficult to test certain things.  Events such as file upload, hover and scroll are not supported yet.  For an updated status of what is supported follow this ticket.

## API testing
**Pro:** Cypress support interacting with an API for end-to-end testing.  There is a built in api testing library that’s simple/easy to use.  This is something selenium/WebDriver.io can’t do without using a different library and extending the framework.
**Con:** If you are just testing an API there is no need for a browser.  Cypress is always running a browser so it may not feel natural.

## Time Travel and Debuggability
**Pro:** Cypress gives you the ability to travel back in time to each command's snapshot like "cy.contains". So, you are able to see what happens before or after some action in a specific command, and it highlights the element and scrolls it into the top of the page displayed in preview.

Cypress provides a good debugging tool that you can check easily why your tests are failing. Your Cypress code runs in the same run loop as your application. It automatically reloads when you make any change to your tests. You have full access to code while the code is running on the page.
Con: None.
