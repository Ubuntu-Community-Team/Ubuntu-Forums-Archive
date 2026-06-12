---
title: "[SOLVED] volume dial controls wrong volume"
date: 2008-11-07
forum: General Help
---

### Post by stephanecharette on 2008-11-07
In pre-8.10, the volume dial on my DELL usb keyboard controlled what I can only guess is called the "master" volume.

But in 8.10, the volume dial now controls the "Recording Capture" volume.  Which I don't use, since I don't record anything from this computer.

How/what do I need to configure to tell Ubuntu that the volume dial on the keyboard should be the "master" volume it controls?

------------------

How I determined what the volume dial controls:

- double click the volume icon in the top-right corner of the gnome panel
- click each tab and observe the little slider bars as I rotate the volume dial up and down
- when device is set to "HDA Intel (Alsa mixer)", on the "Recording" tab, the "Capture" slider bars move up and down to match the rotation of the volume dial.

Thanks in advance.

Stéphane

---

### Post by stephanecharette on 2008-11-07
After trying for a few hours yesterday to figure it out, I finally found the solution 5 minutes after I posted to the forum!  Here is what worked for me:

1) click System -> Preferences -> Sound
2) select the first tab called "Devices"
3) bottom section of that tab is called "Default Mixer Tracks"
4) the "Device" in that section was set to "Capture"; instead, I selected "HDA Intel (Alsa mixer)"
5) select the "Master" device from the scroll window below "Device"
6) click on "Close"

That was it for me.  Volume dial on my keyboard is back to controlling the master volume.

Stéphane

---

### Post by Teh Dust on 2008-11-28
I had the same problem with the volume buttons on my Mac.

Thank you for posting this!

---

### Post by +Eric on 2008-11-28
Yeah, I was having this same problem as well. I hadn't gotten a bug to try and figure out why though, then I just stumbled across your post. Thanks!

---

### Post by dalesd on 2009-03-12
Thanks, Stéphane!

---

### Post by chinchillart on 2009-04-07
Thank you! 
For some reason, after a reboot a lot of gconf-editor values was broken or missing.
Same problem with my Logitech Internet Keyboard.
Solved with your tip!

Curious: I'm still using 8.04.2..

Rob

---

