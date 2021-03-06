# Webpack for ES2015

Sample project for **ES2015 web development** (including code coverage of ES Modules), using **Webpack 2 beta**.


---

## /src/node_modules

Sources are located in folder `/src`, especially in `/src/node_modules`.

Note that the name "**node_modules**" doesn't imply "thirdparty from NPM", it's just [how Node resolves paths](https://nodejs.org/api/modules.html#modules_loading_from_node_modules_folders) (hence why NPM uses it).

That's why `/src/application.js` and modules in `/src/node_modules` subfolders are able to **import other modules using clean paths** like `components/hello` instead of fragile paths like `../../../components/hello/hardcoded.js` without the need for aliasing folder hacks in every tool of your stack.


---

## Webpack

Run `npm start` to launch the development server, then open `http://localhost:8000/webpack-dev-server` in your browser to **see changes in realtime** without the need to build manually or reload the webpage.

Alternatively, run `npm run build` to output files for production (in folder `www`).

You can change the Babel plugins and presets in `/babel.config.js`.


---

## Javascript

The project is configured for **ES2015 javascript** (transpiled to ES5 using [Babel 6](https://babeljs.io)), so you can use features like **arrow functions**, **template strings**, **const**, **let**, etc..

You can use both **ES Modules** (preferably) or **CommonJS**.

[Flow](https://flowtype.org/) **type annotations** are also supported.


---

## CSS

CSS is postprocessed by [PostCSS](http://postcss.org) and [CSSNext](http://cssnext.io).

**Autoprefixer** is configured for IE11+.


### CSS Modules

Webpack is configured to use [Local Scope](https://github.com/webpack/css-loader#css-modules) which generates **globally-unique class names**:

MyComponent.css:

	.class1 {
		color: green;
	}

MyComponent.js:

	import styles from './MyComponent.css';
	console.log(styles.class1);

To disable Local Scope, set `modules: false` in css loader query, in `webpack.config.js`.


---

## Tests & Coverage

[Mocha](https://mochajs.org) tests are located with the module they test, are named `modulename.tests.js`, and are run using `npm test`.

You can change the location of the tests in the root `package.json` settings (if you prefer a centralized `test` folder for example).


---

## Coverage

The coverage report generated by [Istanbul.js](https://istanbul.js.org) is outputted in `/coverage`, and is run using `npm run coverage`.

You can change the output folder and reporters in the root `package.json` settings.


---

## Linting

You can run manually **Eslint** on the codebase using `npm run lint`, and **Flow** using `npm run typecheck`.

I'd also recommend integrating them to your favorite IDE, so you get immediate feedback from the linters.
[Sublime Text](http://www.sublimetext.com), for example, has `Sublimelinter-contrib-eslint` and `Sublimelinter-flow` extensions.


---

