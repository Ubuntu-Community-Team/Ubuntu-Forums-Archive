---
title: "Video and Shudown Problems After Hardy Upgrade"
date: 2008-04-30
forum: Hardware
---

### Post by daemon3 on 2008-04-30
I have two problems that are really annoying.  I didn't have these problems with Gutsy Gibbon.
[LIST]
[*]Problem 1: I can't seem to find my NVidia video driver.  I can see the screen just fine, but I can't get Compiz or 3D games.  When I tried to run [FONT="Courier New"]glxinfo | grep "OpenGL version string"[/FONT], I got the following error:
```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```
I saw a post [here]("http://http://ubuntuforums.org/showthread.php?t=102260") where someone edited their "module" section in xorg.conf.  However, I don't have a "Module" section.  Anything I can do?  I'm trying to upgrade my video driver with envyng, but I need my driver version in order to do that.
[*]Problem 2: Whenever I go to the menu (login screen or user account) and try to shut down, my system hangs (I think where it shuts down the daemons).  Then I have to turn it off manually.
[/LIST]

[CENTER][FONT="Book Antiqua"]**[SIZE="5"][COLOR="Green"]Thank you in advance. :)[/COLOR][/SIZE]**[/FONT][/CENTER]

---

### Post by em3raldxiii on 2008-04-30
Hmm, sounds like you need to enable the restricted driver ... maybe.

Alternatively, you could try a script called Envy written by one of the moderators here ... he goes by tseliot I believe ... and his name is Alberto Milone.  Here's a link to his WIKI page: [https://wiki.ubuntu.com/Tseliot](https://wiki.ubuntu.com/Tseliot)

His script will help you get the manufacturer's driver and it will help you uninstall any botched drivers.  Make sure you read all his documentation :D

Good luck, and let us know if it helps.

---

