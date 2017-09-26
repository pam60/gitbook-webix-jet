## Routing

To manipulate the URL, views have Routers. Webix Jet has four predefined types of routers.

### 1. Hash Router (default)

The app URL is displayed after a hashbang.

~~~js
/* app.js */
var app = new JetApp({
    start: "/Demo/Details",
    router: JetApp.routers.HashRouter,
    views: {
        "Demo": DemoView,
        "Details": DetailsView,
        "Dash": DashView,
        "Toolbar": ToolbarView
    }
}).render();
~~~

### 2. URL Router

The app URL is displayed without a hashbang. Clandestine and cool, but there's a trick with this router. Your server side code should be compatible. (?)

//any examples?

### 3. Store Router
    
With this guy, the app URL isn't displayed at all, but it is stored in the session storage. So no worries, you can still return to the previous and next views as if they are in the URL. This can be useful if you have a multilevel application (apps are subviews of other apps). The Store router is set for the enclosed apps because there's only one address bar and it's already taken by the outer app. Suppose you have have closed an app module with a deep level of subviews and expect to be in the same place of this app when you switch to it again. The Store router allows this. 

~~~js
var app1 = new JetApp({
    start: "/Form",
    router: JetApp.routers.StoreRouter, //у меня не заработала демо,наверное я неправильно что-то поняла
    views: {
        "Form": FormView,
        "Details": DetailsView
    }
});

const PageView = () => ({
    rows: [app1]
});

var app2 = new JetApp({
    start: "/Page",
    router: JetApp.routers.HashRouter,
    views: {
        "Page": PageView
    }
}).render();
~~~

### 4. Empty Router

If you don't want this behavior from the app, there's the Emplty router for you. The app URL isn't displayed and isn't stored. It's used for nested apps because there is only one address bar. [Check out the demo](https://git.webix.io/mkozhukh/wjet/src/master/samples/06_highlevel.html).

### 5. Custom Routers

If these four routers aren't what you want, you can define your own.

//HELP NEEDED WITH THIS AS WELL