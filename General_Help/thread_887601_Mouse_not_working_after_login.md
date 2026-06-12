---
title: "Mouse not working after login"
date: 2008-08-12
forum: General Help
---

### Post by gausie on 2008-08-12
Hi everyone

When I'm logging in the mouse is fine, but once I've logged in, the mouse is non responsive at just sits in the center of the screen.

I've tried dpkg-reconfigure xserver-xorg, and it didn't work.

Any suggestions?

Gausie

---

### Post by bc90021 on 2008-08-12
What type of mouse is it?  Wired, wireless, or bluetooth?

If wired, try this in a console:

ln -s /dev/psaux /dev/mouse

It may be that your device isn't being seen by X and/or GNOME.

That's the only thing I can think of that you haven't already tried.

If it's wireless or bluetooth, I'll not be of much help - I can't get my BT mouse (or keyboard) to work in HH.

---

### Post by gausie on 2008-08-12
Before I do that, it is USB mouse, so is psaux the right device to link?

Gausie

---

### Post by bc90021 on 2008-08-12
It should be, yes.  Even if it's not, adding that link won't make things worse, and you can always delete the link with rm /dev/mouse.

(You'll have to be sudo in both cases, I forgot to mention that.)

---

### Post by gausie on 2008-08-12
Worked it out!

I noticed a black flash before the mouse stopped working, and realised its a startup program that is crashing and sending the mouse down with it. Disabled that from the Sessions GUI, and it works fine now!

Gausie

---

