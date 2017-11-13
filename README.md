<h1 align="center">
    <a href="https://devexpress.github.io/testcafe">
        <img src="https://raw.github.com/DevExpress/testcafe/master/media/logo.png" alt="testcafe" />
    </a>
</h1>

<p align="center">
<a href="https://ci.appveyor.com/project/DevExpress/testcafe"><img alt="Functional Windows desktop" src="https://ci.appveyor.com/api/projects/status/ftelkyuiji8lyadf?svg=true"></a>
<a href="https://travis-ci.org/DevExpress/testcafe"><img alt="All Travis tasks (server, client, functional: mobile, macOS, Edge)" src="https://travis-ci.org/DevExpress/testcafe.svg"></a>
<a href="https://www.npmjs.com/package/testcafe"><img alt="NPM Version" src="https://img.shields.io/npm/v/testcafe.svg" data-canonical-src="https://img.shields.io/npm/v/testcafe.svg" style="max-width:100%;"></a>
</p>

<p align="center">
<i>A Node.js tool to automate end-to-end web testing.<br/>Write tests in JS or TypeScript, run them and view results.</i>
</p>

<p align="center">
<a href="https://devexpress.github.io/testcafe">https://devexpress.github.io/testcafe</a>
</p>

----

* **Works on all popular environments**: TestCafe runs on Windows, MacOS, and Linux. It supports desktop, mobile, remote and cloud [browsers](https://devexpress.github.io/testcafe/documentation/using-testcafe/common-concepts/browser-support.html) (UI or headless).
* **1 minute to set up**: You [do not need WebDriver](https://devexpress.github.io/testcafe/faq/#i-have-heard-that-testcafe-does-not-use-selenium-how-does-it-operate) or any other testing software. Install TestCafe with one command, and you are ready to test: `npm install -g testcafe`
* **Free and open source**: TestCafe is free to use under the [MIT license](https://github.com/DevExpress/testcafe/blob/master/LICENSE). [Plugins](#plugins) provide custom reports, integration with other tools, launching tests from IDE, etc. You can use the plugins made by the GitHub community or make your own.

![Install TestCafe and Run a Test](https://raw.githubusercontent.com/DevExpress/testcafe/master/media/install-and-run-test.gif)

<p align="center">
<i>Running a sample test in Safari</i>
</p>

## Table of contents

* [Features](#features)
* [Getting Started](#getting-started)
* [Documentation](#documentation)
* [Community](#community)
* [Badge](#badge)
* [Contributing](#contributing)
* [Plugins](#plugins)
* [License](#license)
* [Creators](#creators)

## Features

**Stable tests and no manual timeouts**<br/>
TestCafe automatically waits for page loads and XHRs before the test starts and after each action.
It also features smart test actions and assertions that wait for page elements to appear.
You can change the maximum wait time.
If elements load faster, tests skip the timeout and continue.

**Latest JS and TypeScript support**<br/>
TestCafe supports the latest JavaScript features, including ES2017 (for example, async/await).
You can also [use TypeScript](https://devexpress.github.io/testcafe/documentation/test-api/typescript-support.html)
if you prefer a strongly typed language.

**Detects JS errors in your code**<br/>
TestCafe reports JS errors that it finds on the webpage.
Tests automatically fail because of that.
However, you can disable this.

**Concurrent tests launch**<br/>
TestCafe can open multiple instances of the same browser to run parallel
tests which decreases test execution time.

**PageObject pattern support**<br/>
The TestCafe's [Test API](https://devexpress.github.io/testcafe/documentation/test-api/)
includes a high-level selector library, assertions, etc.
You can combine them to implement readable tests with the [PageObject pattern](https://devexpress.github.io/testcafe/documentation/recipes/using-page-model.html).

```js
const macOSInput = Selector('.column').find('label').withText('MacOS').child('input');
```

**Easy to include in a continuous integration system**<br/>
You can run TestCafe from a console, and its reports can be viewed in a CI system's interface
(TeamCity, Jenkins, Travis & etc.)

## Getting Started

### Installation

Ensure that [Node.js](https://nodejs.org/) (version 4 or newer) and [npm](https://www.npmjs.com/) are installed on your computer before running it:

```sh
npm install -g testcafe
```

### Creating the Test

As an example, we are going to test the [https://devexpress.github.io/testcafe/example](https://devexpress.github.io/testcafe/example) page.

Create a `.js` or `.ts` file on your computer.
Note that it needs to have a specific structure: tests must be organized into fixtures.
You can paste the following code to see the test in action:

```js
import { Selector } from 'testcafe'; // first import testcafe selectors

fixture `Getting Started`// declare the fixture
    .page `https://devexpress.github.io/testcafe/example`;  // specify the start page


//then create a test and place your code there
test('My first test', async t => {
    await t
        .typeText('#developer-name', 'John Smith')
        .click('#submit-button')

        // Use the assertion to check if the actual header text is equal to the expected one
        .expect(Selector('#article-header').innerText).eql('Thank you, John Smith!');
});
```

### Running the Test

Call the following command in a command shell.
Specify the [target browser](https://devexpress.github.io/testcafe/documentation/using-testcafe/command-line-interface.html#browser-list)
and [file path](https://devexpress.github.io/testcafe/documentation/using-testcafe/command-line-interface.html#file-pathglob-pattern).

```sh
testcafe chrome test1.js
```

TestCafe opens the browser and starts executing the test.

> Important! Make sure to stay in the browser tab that is running tests.
> Do not minimize the browser window. Tests are not guaranteed to execute correctly
> in inactive tabs and minimized browser windows because they switch to a lower resource consumption mode.

### Viewing the Results

TestCafe outputs the results into a command shell by default. See [Reporters](https://devexpress.github.io/testcafe/documentation/using-testcafe/common-concepts/reporters.html)
for more information. You can also use [plugins](#plugins) to customize the reports.

![Test Report](docs/articles/images/report.png)

Read the [Getting Started](https://devexpress.github.io/testcafe/documentation/getting-started/) page for a more detailed guide.

## Documentation

Go to our website for full [documentation](http://devexpress.github.io/testcafe/documentation/using-testcafe/) on TestCafe.

## Community

Follow us on [Twitter](https://twitter.com/DXTestCafe). We post TestCafe news and updates, several times a week.

## Badge

Show everyone you are using TestCafe: ![Tested with TestCafe](https://img.shields.io/badge/tested%20with-TestCafe-2fa4cf.svg)

To display this badge, add the following code to your repository readme:

```html
<a href="https://github.com/DevExpress/testcafe">
    <img alt="Tested with TestCafe" src="https://img.shields.io/badge/tested%20with-TestCafe-2fa4cf.svg">
</a>
```

## Contributing

Report bugs and request features on our [issues page](https://github.com/DevExpress/testcafe/issues).<br/>
Ask questions and participate in discussions on the [discussion board](https://testcafe-discuss.devexpress.com/).<br/>
For more information on how to help us improve TestCafe, see the [CONTRIBUTING.md](https://github.com/DevExpress/testcafe/blob/master/CONTRIBUTING.md).

You can use these plugin generators to create your own plugins:

* [Build a browser provider](https://devexpress.github.io/testcafe/documentation/extending-testcafe/browser-provider-plugin/)
  to set up tests on your on-premises server farm, to use a cloud testing platform, or to start your local browsers in a special way. Use this [Yeoman generator](https://www.npmjs.com/package/generator-testcafe-browser-provider) to write only a few lines of code.
* To [build a custom reporter](https://devexpress.github.io/testcafe/documentation/extending-testcafe/reporter-plugin/)
  with your formatting and style, check out this [generator](https://www.npmjs.com/package/generator-testcafe-reporter).

If you want your plugin to be listed below, [send us a note in a Github issue](https://github.com/DevExpress/testcafe/issues/new).

## Plugins

TestCafe developers and community members made these plugins:

* **Browser Providers**<br/>
  Allow you to use TestCafe with cloud browser providers and emulators.
  * [SauceLabs provider](https://github.com/DevExpress/testcafe-browser-provider-saucelabs) (by [@AndreyBelym](https://github.com/AndreyBelym))
  * [BrowserStack provider](https://github.com/DevExpress/testcafe-browser-provider-browserstack) (by [@AndreyBelym](https://github.com/AndreyBelym))
  * [Nightmare headless provider](https://github.com/ryx/testcafe-browser-provider-nightmare) (by [@ryx](https://github.com/ryx))
  * [fbsimctl iOS emulator](https://github.com/Ents24/testcafe-browser-provider-fbsimctl) (by [@ents24](https://github.com/Ents24))
  * [Electron](https://github.com/DevExpress/testcafe-browser-provider-electron) (by [@AndreyBelym](https://github.com/AndreyBelym))
  * [Puppeteer](https://github.com/jdobosz/testcafe-browser-provider-puppeteer) (by [@jdobosz](https://github.com/jdobosz))

* **Framework-Specific Selectors**<br/>
  Work with page elements in a way that is native to your framework.
  * [React](https://github.com/DevExpress/testcafe-react-selectors) (by [@kirovboris](https://github.com/kirovboris))
  * [Angular](https://github.com/DevExpress/testcafe-angular-selectors) (by [@miherlosev](https://github.com/miherlosev))
  * [Vue](https://github.com/devexpress/testcafe-vue-selectors) (by [@miherlosev](https://github.com/miherlosev))
  * [Aurelia](https://github.com/miherlosev/testcafe-aurelia-selectors) (by [@miherlosev](https://github.com/miherlosev))

* **Plugins for Task Runners**<br/>
  Integrate TestCafe into your project's workflow.
  * [Grunt](https://github.com/crudo/grunt-testcafe) (by [@crudo](https://github.com/crudo))
  * [Gulp](https://github.com/DevExpress/gulp-testcafe) (by [@inikulin](https://github.com/inikulin))

* **Custom Reporters**<br/>
  View test results in different formats.
  * [TeamCity](https://github.com/Soluto/testcafe-reporter-teamcity) (by [@nirsky](https://github.com/nirsky))
  * [Slack](https://github.com/Shafied/testcafe-reporter-slack) (by [@Shafied](https://github.com/Shafied))
  * [NUnit](https://github.com/AndreyBelym/testcafe-reporter-nunit) (by [@AndreyBelym](https://github.com/AndreyBelym))
  * [TimeCafe](https://github.com/jimthedev/timecafe) (by [@jimthedev](https://github.com/jimthedev))

* **Test Accessibility**<br/>
  Find accessibility issues in your web app.
  * [axe-testcafe](https://github.com/helen-dikareva/axe-testcafe) (by [@helen-dikareva](https://github.com/helen-dikareva))

* **IDE Plugins**<br/>
  Run tests and view results from your favorite IDE.
  * [Visual Studio Code](https://github.com/romanresh/vscode-testcafe) (by [@romanresh](https://github.com/romanresh))
  * [SublimeText](https://github.com/churkin/testcafe-sublimetext) (by [@churkin](https://github.com/churkin))

* **ESLint**<br/>
  Use ESLint when writing and editing TestCafe tests.
  * [ESLint plugin](https://github.com/miherlosev/eslint-plugin-testcafe) (by [@miherlosev](https://github.com/miherlosev))

## Thanks to BrowserStack

We are grateful to BrowserStack for providing the infrastructure that we use to test code in this repository.

<a href="https://www.browserstack.com/"><img alt="BrowserStack Logo" src="https://raw.github.com/DevExpress/testcafe/master/media/BrowserStack.png"/></a>

## License

Code released under the [MIT license](LICENSE).

## Creators

Developer Express Inc. ([https://devexpress.com](https://devexpress.com))