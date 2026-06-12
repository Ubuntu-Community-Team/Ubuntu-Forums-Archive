---
title: "kde switch lcd off??"
date: 2009-12-20
forum: Hardware
---

### Post by jerrylamos on 2009-12-20
kde in kubuntu how do I switch the lcd off when using an external monitor?

This is dead pipe simple with gnome, just do System > Preferences > Display and fill in the panel.

With kde I get lost in tons and tons of menus but see no way just to turn the lcd off, saving its lifetime, and use the external monitor.

Debian LXDE desktop is even simpler, fewer keystrokes yet.

Any hints on how to get kde to do this simple user function?

Right now I open a terminal session and type in:

xrandr --output LVDS --off

Isn't there a GUI way to do this in kde?  There is in gnome.

Appreciate any help

Jerry

---

### Post by Zorael on 2009-12-21
There's krandrtray which also provides the same basic functionality that System Settings -> Display does, which equates to "very limited". I'm not sure why it's not getting more attention. There have been some mailing list discussions about whether to replace it with a plasma widget, but I'm not sure if it led to anything.

There's **arandr** in the repositories if you want a replacement graphical tool.

If you only want to toggle it, you can probably also set up a On/Off Switch plasma widget. I have one set up to send stop and continue signals to Chromium, so that it won't use cpu time when I'm not using it. (**edit**) While unofficial, there are packages of it available from [Sam Rog's ppa](https://launchpad.net/~samrog131/+archive/ppa).

---

### Post by jerrylamos on 2009-12-21
> **Zorael said:**
> There's krandrtray which also provides the same basic functionality that System Settings -> Display does, which equates to "very limited". 

Thanks, I took a look at "xrandr" and couldn't tell what to do with it.

Fumbled around and found xrandr --output LVDS --off which worked.  I don't know if I'll be able to remember that command line...just made it into a command line exec.

I had thought KDE would be all about graphical actions but somehow in the very basic case of handling laptop LCD's, both Gnome and LXDE have a graphical solution while apparently KDE doesn't.

Thanks again, Jerry

---

