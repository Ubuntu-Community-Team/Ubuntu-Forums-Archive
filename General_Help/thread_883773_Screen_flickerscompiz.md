---
title: "Screen flickers/compiz"
date: 2008-08-08
forum: General Help
---

### Post by snkngshps on 2008-08-08
I have kind of an annoying problem. When I play games, especially in full screen mode, I get really bad screen flickering. It's so bad, it's mostly unplayable. I posted about it once before and I was told to disable compiz when I play games, which worked. This is annoying in itself to have to disable/re-enable desktop effects every time a play a game, but what's even worse is when I turn off desktop effects it resets all of my compiz settings. So when I turn Advanced Desktop Effects back on it's set back to its default settings and I have to go back through and set it all up again.

What I'd really like to do is solve the flicker problem without having to disable compiz every time, but if that's absolutely not possible is there a way I can keep my compiz settings each time I disable/enable Desktop Effects?

---

### Post by halln on 2008-08-08
> **snkngshps said:**
> I have kind of an annoying problem. When I play games, especially in full screen mode, I get really bad screen flickering. It's so bad, it's mostly unplayable. I posted about it once before and I was told to disable compiz when I play games, which worked. This is annoying in itself to have to disable/re-enable desktop effects every time a play a game, but what's even worse is when I turn off desktop effects it resets all of my compiz settings. So when I turn Advanced Desktop Effects back on it's set back to its default settings and I have to go back through and set it all up again.

What I'd really like to do is solve the flicker problem without having to disable compiz every time, but if that's absolutely not possible is there a way I can keep my compiz settings each time I disable/enable Desktop Effects?


I think it is something to do with your graphics card and better to install compiz fusion icon (add-remove) and just to metacity if you want to game.
:)

---

### Post by yaise on 2009-06-30
I just installed 9.04,jaunty with a ATI Radeon 4870 graphics card and am having the same problem. Tested this with Chromium BSU. Flickering goes away when Desktop effects are disabled.
Has anyone found a workaround to keep desktop effects and get rid of the flickering

TIA

---

### Post by t4thfavor on 2009-06-30
I had flickering due to an incorrect refresh rate, maybe check there.

---

### Post by QIII on 2009-06-30
Go to Applications | Add/Remove and type "compiz" in the search box.

One of the first things will be Compiz Fusion Icon.

When you install that, you will get the icon on your panel.

Double click it to start, then you can use the new icon that appears on your panel to enable and disable Compiz/Metacity on-the-fly in the menu item "Select Window Manager".

MetaCity may work better for you when you are running videos.  It does for me.  Probably a combination of Compiz and my video card/driver.  When you are done with your video, just switch back to Compiz.

I don't lose my Compiz settings when I do this, but your mileage may vary.

---

### Post by 3rdalbum on 2009-07-01
> **snkngshps said:**
> What I'd really like to do is solve the flicker problem without having to disable compiz every time

Then you need an Nvidia graphics card. ATI's drivers cause the flickering problem.

Compiz isn't just a set of effects, it's a window manager. The way Ubuntu "turns off" Compiz is by loading the regular Gnome window manager, which is called Metacity. It might be doing some other stuff too which might be causing your "losing all Compiz settings" problem.

You can manually switch to Metacity by pressing Alt-F2 and typing this:

```
metacity --replace
```

And switch to Compiz by pressing Alt-F2 and typing:

```
compiz --replace
```

Using this method I have not lost any Compiz settings.

---

### Post by yaise on 2009-07-01
I installed the compiz fusion icon. set it to compiz mode.
Set the desktop visual effects to its highest mode, and there was no flickering in Chromium BSU. Thanks!

Will have to wait n see what happens when I run a more graphic intensive program.

---

