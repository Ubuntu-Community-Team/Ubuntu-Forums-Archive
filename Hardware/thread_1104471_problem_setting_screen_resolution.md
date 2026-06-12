---
title: "problem setting screen resolution"
date: 2009-03-23
forum: Hardware
---

### Post by mysticaltopher on 2009-03-23
I installed Ubuntu on a room-mates desktop computer and it has a Nvidia TNT2 graphics card....I know, not compatible. I was wondering if there is a way to boost the resolution beyond the 800x600 to 1024x768? I looked at his xorg.conf file through gedit, (I'm not sure this is where I would even fix the problem) and it looks like this:

Section "Device"
Identifier "Configured Video Device"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection

Do I need to delete either the screen or monitor sections or can I add in the new screen resolution to this file? Please help, I've been trying to fix this problem for 3 weeks now....Thanks!

---

### Post by norwoods on 2009-03-23
can you install envyng and use that to install an nvidia 71.86.09 driver?
can you install nvidia-settings and use that to mess with resolution?

---

### Post by mysticaltopher on 2009-03-23
what is envyng and how do i install it?  i did install the nvidia 71.86.09 driver but it fails to load on start-up....haven't messed with the nvidia-settings yet, is there a GUI for it or is it run through the terminal....Thanks!

---

### Post by norwoods on 2009-03-24
> **mysticaltopher said:**
> what is envyng and how do i install it?  i did install the nvidia 71.86.09 driver but it fails to load on start-up....haven't messed with the nvidia-settings yet, is there a GUI for it or is it run through the terminal....Thanks!

envyng is a driver installer that you can install with synaptic:
System-->Administration-->Synaptic Package Manager

the best way to run nvidia-settings is from the terminal so that you have admin privilege:
gksu nvidia-settings

---

