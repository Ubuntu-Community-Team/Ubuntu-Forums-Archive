---
title: "Issues with Wacom Intuos3 in Gimp"
date: 2011-09-14
forum: Hardware
---

### Post by Kanvis on 2011-09-14
Hi im recently new to ubuntu and to linux in general.  Im having a blast but I came across this issue.

In gimp 2.6, when I change my stylus setting to allow pressure sensitivity, it will allow me to draw a line EVERY OTHER stroke. For every one stroke, the next one will have no response.  When the sensitivity is off, there is no issues. It not a issue with the Wacom from my tests, the the device is working properly, but I think it my be a setting or something that is causing this issue. I have search here and the web for an answer, but to no avail.  

Thanks in advance

---

### Post by Favux on 2011-09-14
Hi Kanvis,

Welcome to Ubuntu forums!

Your problem has been seen before.  I assume you are using Natty (11.04)?  It appears to be some Compiz/Unity bug, maybe involving Gtk 2.

One solution is described here:  [http://ubuntuforums.org/showthread.php?t=1767404&highlight=vblank+gimp](http://ubuntuforums.org/showthread.php?t=1767404&highlight=vblank+gimp)

Another thing to try is when you are at the log in screen select Classic Mode or Classic without effects (on the bottom of the screen).  Hopefully it will be fixed in Oneiric with more work on the Unity plug-in to Compiz.  Plus it changes over to Gtk 3.

---

