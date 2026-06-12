---
title: "Help virtual Box!"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by phr33k-dc on 2009-03-05
installed xp performance edition march '09. when i boot it uo i cant get the mouse working because i have to download guest actions.iso or something. i have downloaded it and its on my desktop so now what do i do with it?

thanks in advanced

---

### Post by bluelamp999 on 2009-03-05
Hey fellow Dub dweller,

Just to be clear, are you running VirtualBox on an Ubuntu host and running XP as a guest?

If so, you should already have VBoxGuestAdditions.iso, it's part of the VirtualBox download/install.

It's probably at /usr/share/virtualbox but if it ain't then search for it...

If the only VBoxGuestAdditions.iso file you have is the one you have on your desktop you can still try the below...

Fire up your XP virtual machine and go... Devices > Mount CD/DVD ROM > CD/DVD ROM Image... Then use Add and select your VBoxGuestAdditions.iso file. This now appears as a CD drive on your virtual machine, probably drive D:.

If the CD doesn't autostart, go to your CD drive (VirtualBox Guest Additions (D:)) and run VBoxWindowsAdditions.exe.

This should then install and you'll have mouse capture, shared folders and other handy stuff.

Good luck...

---

