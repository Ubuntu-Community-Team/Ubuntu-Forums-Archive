---
title: "Samsung N150 Plus touchpad recognition"
date: 2010-07-30
forum: Hardware
---

### Post by PaulWhipp on 2010-07-30
I've just converted a friends N150 to Linux and I thought I'd tweak the touchpad so it doesn't get in the way when typing. The configuration options were missing - no touchpad tab under the mouse preferences.

I tried the voria/ppa but this does not seem to do anything regarding the touchpad.

Installing gsynaptic and the pointing device recommended tools had exactly the same problem and I could not tell tpconfigure which device was the touchpad. So after much wasted time:

xinput list
shows an ImPS/2 Logitech Wheel Mouse and Macintosh mouse button emulation so it seems that these are the "touchpad"

Am I right?

Does anyone know how I can get the touchpad set up and configured properly?

---

### Post by kgas on 2010-07-30
there is a samasung tools application in the repo or get it from [lauchpad](https://launchpad.net/samsung-tools) with that you can disable the touch pad while typing.

---

### Post by PaulWhipp on 2010-07-30
Thanks I got that. It adds the "samsung tools preferences" but there is nothing there at all about the touchpad so I cannot see how to disable it while typing (which would be half the battle - then if I could just disable or adjust the sensitivity of the tap simulation of the mouse clicks I could live with it).

I have installed the xserver-xorg-input-synaptics too but can't see a difference. As far as ubuntu is concerned the touchpad appears to be a mouse :(

---

### Post by kgas on 2010-08-01
with that tools you can set the function keys to activate and deactivate the mouse pad.I will post the screen shot soon.

---

### Post by Nafbuntu on 2010-10-31
Have the exact same netbook.

Fn + F10 seems to do the trick for me to disable/enable touchpad

---

### Post by avidscavenger on 2011-01-09
The lack of ability to have the touchpad automatically detect accidental brushes while typing was about the most annoying thing on the N150. Manually activating and de-activating is way too painful. So I hacked up a quick solution.  To use it, simply run the attached python script in the background, eg:

> sudo nohup lock_mouse_on_keystroke.py > /dev/null &I've put a few comments in it which should make it comprehensible to anyone with very basic understanding of programming in python. Put very simply, it locks the mouse for half a second (change the value of TIMEOUT if this is too long or short) following any keystrokes, then unlocks it again.

---

### Post by x43 on 2011-03-29
Thanks alot. I was having the same problem and your script seems to be the only available solution I could find!

---

