##IN PROGRESS
##An Ionic 1 App example with the [X] and [X] ngCordova Plugins
(that works in the browser, simulator, and on an iOS device)

When building my first Ionic app I had trouble finding and example that worked across platforms and I also ran into some small details that tripped me up, especially when looking to make my app work on the next platform (i.e. it worked in simulator! why isn't it working on the iphone?!)... so here's a demo that I've verified works across the browser, simulator, and on an iOS device.


Building this project
=====================

Make sure the `ionic` utility is installed:

```$ npm install -g ionic
```

Make sure the `cordova` is installed:
```npm install -g cordova OR check version (cordova -v)
```
```ionic start [app_name] [ionic starter type: blank, tabs, or sidemenu]
```
```cd [app_name]
```
open the js/app.js file:
add ```window.cordova.plugins &&` to the run block, so your full run block in your app.js file looks like this:

.run(function($ionicPlatform) {
  $ionicPlatform.ready(function() {
    if (window.cordova && window.cordova.plugins && window.cordova.plugins.Keyboard) {
      cordova.plugins.Keyboard.hideKeyboardAccessoryBar(true);
      cordova.plugins.Keyboard.disableScroll(true);
    }
    if (window.StatusBar) {
      StatusBar.styleDefault();
    }
  });
})
```
```npm init -y
```

Knowing that we are going to use ngCordova plugins, we're going to go ahead and add them now
```bower install ngCordova
```
+ add ngCordova script to index.html file above the cordova.js
```<script src="lib/ngCordova/dist/ng-cordova.js"></script>
```

In your app.js file add the ngCordova module as a dependencies to your app module:

```.module('app_name', ['ionic', 'ngCordova'])
```

Add script tags for the cordova plugins you want to use (see [docs]() for .git addresses for other plugins):
EmailComposer: cordova plugin add https://github.com/katzer/cordova-plugin-email-composer.git


We're going to use EmailComposer and X because they are a good combination for a basic app and EmailComposer requires us to test on a device.

Setup git
```git init
touch .gitignore
```
Go make a repo from your github account, then
``git remote add origin [your repo address]
``
``git push -u origin master
``

**Bonus - Using Ionic Modal**
npm install ionic-modal-component
+ add script to index.html file
<script src="dist/ionic-modal-component.js"></script>

**Bonus - Manipulating Time Entry and Formatting**
Moment.js
npm install --save moment
+ add script to index.html file
<script src="https://cdnjs.cloudflare.com/ajax/libs/moment.js/2.9.0/moment.min.js"></script>

Angular-moment
npm install angular-moment --save #angular-moment
+ add script to index.html file
<script src="http://cdnjs.cloudflare.com/ajax/libs/angular-moment/0.9.0/angular-moment.min.js"></script>

Add the module angularMoment as a dependency to your app module:
.module('app_name', ['ionic', 'ngCordova', 'angularMoment'])

<!-- <script src="components/moment/moment.js"></script>
<script src="components/angular-moment/angular-moment.js"></script> -->

SQLite: cordova plugin add https://github.com/litehelpers/Cordova-sqlite-storage.git
