---
title: "LCD does not turn off when lid closed"
date: 2010-03-22
forum: Hardware
---

### Post by snivek on 2010-03-22
I have a Dell Latitude E6400 with an Intel GMA graphics card.  When I shut the lid of my laptop the screen does not go off.  If I kill gnome-power-manager it does turn off.  Two questions:

A) Does anyone know of a fix so I do not have to kill GPM?
B) What do I lose if GPM is not running?  I killed it everything still seems to work as I would expect...

Thanks!

--Kevin

---

### Post by _h_ on 2010-03-22
System -> Preferences -> Power Management.

What is your setting for "When laptop lid is closed"?

---

### Post by snivek on 2010-03-22
"Blank screen"

---

### Post by snivek on 2010-05-04
I played with this a little more and when the lid is up everything works as it should.  Screensaver comes on and LCD eventually goes completely off, backlight and all.  I then closed the lid very slowly and looked/watched carefully what happened when I did.  It appears that the login/password box is appearing on the screen when the lid closes.  The login box stays displayed for a few minutes and then goes away but the backlight stays on.  

Can anyone give me some advice here?  Even if it's how to turn on some logging to monitor what is going on.  Thanks!

--Kevin

---

### Post by snivek on 2010-05-05
Looks like I am experiencing this but - [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/41994](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/41994)

Still exists on Lucid!

---

