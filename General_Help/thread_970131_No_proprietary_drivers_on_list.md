---
title: "No proprietary drivers on list"
date: 2008-11-03
forum: General Help
---

### Post by lhansen on 2008-11-03
Just upgraded to intrepid. Everything was working fine until I changed my screen resolution to work with an external monitor. Then the desktop effects stopped working. I tried to turn them back on and got an error message when looking for the drivers. I went to look at my hardware drivers (system>administration>Hardware Drivers), and there were no drivers on the list. Where did they go? How do I get them back?

Thanks

---

### Post by sharkster2007 on 2008-11-03
If it is an NVIDIA card The following worked for my NVIDIA 6600GT

Web source for .deb packages is [http://packages.ubuntu.com/intrepid/...-kernel-source](http://packages.ubuntu.com/intrepid/...-kernel-source)

Quote:
I have installed [COLOR="SeaGreen"]dkms_2.0.20.4-0ubuntu_all.deb[/COLOR] & [COLOR="SeaGreen"]nvidia-173-kernel-source_173.14.12-1-0ubuntu4_i386.deb[/COLOR] & [COLOR="SeaGreen"]nvidia-glx-173_173.14.12-1-0ubuntu4_i386[/COLOR] as these are the only parts required by 8.10 the other dependancies are already installed as standard. (double click the .deb files on desktop to install them)

Then go to:

SYSTEM>ADMINISTRATION>HARDWARE DRIVERS select NVIDIA ACCELERATED GRAPHICS DRIVER (VERSION 173) click enable, an arrow should appear asking you to restart your system

After restarting your system the driver will enable, select your desktop effects from appearances and your done enjoy

PS: I am a brand new user to ubuntu but this worked for me, hope it helps you.

---

### Post by lhansen on 2008-11-04
I have an Intel 915 card. According to [https://help.ubuntu.com/community/RestrictedDrivers]("https://help.ubuntu.com/community/RestrictedDrivers") I don't need any restricted drivers.

I followed instructions at [http://ph.ubuntuforums.com/showthread.php?t=766683&highlight=xserver-xorg-video-intel]("http://ph.ubuntuforums.com/showthread.php?t=766683&highlight=xserver-xorg-video-intel"), but that didn't work.

I then tried using my last xorg.conf, but intrepid didn't like it and I had to log in in low graphics mode and restore the newest version of the file.

Any thoughts? Thanks for your help.

---

### Post by lhansen on 2008-11-04
Okay, looks like the xorg.conf was the problem. When I tried a previous version I used a faulty backup. I'm now using a version that actually worked in hardy, and I have all of my desktop effects.

Hopefully this helps someone else.

---

