
# pxt-interval ![Build Status Abzeichen](https://github.com/ractive/pxt-interval/workflows/MakeCode/badge.svg)

If you want to repeatedly do something in your game, you can add a callback method to `game.onUpdateInterval` like
`game.onUpdateInterval(500, () => doSomething())`. But you cannot unsubscribe this callback from being executed - never.

If you want to do something periodically but only for a certain time, this extension can help you. A callback handler
that is registered to be executed in a given interval can also be unsubscribed again. The call to `Interval.on` returns
a function that can be called to do the unsubscription:

```
const unsubscribe = Interval.on(500, () => doSomething());
...
unsubscribe();
```

Here an example how to fire projectiles every 500 milliseconds for 3 seconds:
```
// Shoot for 3 seconds
const unsubscribe = Interval.on(500, () => sprites.createProjectileFromSprite(myImage, mySprite, 50, 0));
setTimeout(() => unsubscribe(), 3000);
```

## Using it in your project

To use this extension in your project, choose "Advanced > Extensions..." and enter `https://github.com/ractive/pxt-interval` in the search box.

This extension uses the [pxt-heap](https://github.com/jwunderl/pxt-heap) extension to easily fetch the next callback handler that should be executed.

#### Metadata

* for PXT/arcade
<script src="https://makecode.com/gh-pages-embed.js"></script><script>makeCodeRender("{{ site.makecode.home_url }}", "{{ site.github.owner_name }}/{{ site.github.repository_name }}");</script>
