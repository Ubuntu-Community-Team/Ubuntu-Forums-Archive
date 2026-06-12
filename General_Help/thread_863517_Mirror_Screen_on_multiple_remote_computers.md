---
title: "Mirror Screen on multiple remote computers?"
date: 2008-07-18
forum: General Help
---

### Post by TagUrIt on 2008-07-18
Does anyone know of a way to mirror the contents of one screen onto many other screens (over a network, not physically attached)?  What I mean is that the other computers won't actually be doing anything besides getting the data and displaying it.

What I need to do is to take, for example, an OpenOffice presentation and have it run on one computer, but make it possible for everyone else in the room to see the exact thing on the monitor in front of them.  (I don't want the users to be able to control the screen via mouse or keyboard.  Preferably, these will be "locked" away from the user's control.)  All of the boxes involved are running 7.10 (some Ubuntu, some Kubuntu).  If needed, I can upgrade them all to a newer version of the same desktop environment.

I had thought to have all of the boxes ssh into the one and then try to export the display, but I get the feeling that only one person would have the screen at any given time.

Thanks. :)

(Sorry if this is in the wrong area, but I couldn't decide if this was a video or networking topic, or maybe even something else.)

Edit:
The boxes that will have the images displayed on them are "dumb" boxes that users will have no interaction with.  If the solution involves installing something that takes all power away from the person sitting at the machine, I have no problems with that.  We can always reinstall Ubuntu afterwards. :)

---

### Post by jimv on 2008-07-18
You can use VNC to do this.  Just go to System > Preferences > Remote Desktop.  Check "Allow other users to view your desktop" and uncheck "Allow other users to control your desktop".

Then connect to the machine using VNC clients on the workstation.

They'll see it, but that can't do anything to it.

---

