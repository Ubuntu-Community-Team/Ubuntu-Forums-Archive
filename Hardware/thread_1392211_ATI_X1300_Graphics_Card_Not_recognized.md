---
title: "ATI X1300 Graphics Card Not recognized"
date: 2010-01-27
forum: Hardware
---

### Post by 3llz on 2010-01-27
Hey All, 
I recently installed Ubuntu 9.10 on my laptop. I have an ATI X1300 Mobility Graphics card and it had not been detected. Graphic Effects cannot be enabled. I would appreciate step by step instructions to help me solve this problem. 

Another thing that I would like to know is if there is anything like Visual Studio for Ubuntu.

Thanks in advance to anyone who does reply.

---

### Post by RRF2525 on 2010-01-28
Still having issues?  If so, what have you done so far in trying to enable your video driver?

I'm new to Ubuntu but working through similar problems right now with my NVIDIA and am not getting response on this forum.  So, maybe I can help you instead!?  Worth a try at least...

My first step is to take a look at System > Administration > Hardware Drivers and see if there are any devices recognized and the recommended driver(s) for the device.  Even then you're not necessarily home free as xorg.conf will have to be edited if I'm not mistaken.  (That's where I'm at in trying to get the latest drivers (190) recognized from NVIDIA).

As for a Linux solution for Visual Studio I'd go to the PM (Package Manager) via System > Administration > Synaptic Package Manager and troll through the available packages for your distro.  It's a great way to learn about what you have and find kewl stuff that you may want to add...

Cheers!

---

### Post by coldraven on 2010-01-29
AFAIK your card cannot use ATIs proprietary driver because it is not compatible with the version of Xorg in 9.04 and 9.10.
I cannot remember which Xorg we are using but if you go to ATI and look in the Legacy section it has some info.
So my laptop has an X1250 card and is working fine with Compiz but not  for gaming as the 3D is too slow
Search for my posts and you will get the general idea.
I'm thinking of re-installing XP and selling this machine, then buy one with an NVidia card.
You could of course try Ubuntu 8.04 or another distro like Suse .
Good luck!

---

### Post by mjones141 on 2011-05-23
I am having the same problem on Ubuntu Studio with my X1550 card. I try to run ATI Config but it says no supported adapters found.
I don't understand!! This is driving me nuts!

---

