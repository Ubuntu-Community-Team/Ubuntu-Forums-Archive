---
title: "Cannot make Thinkpad T400 work !"
date: 2008-10-23
forum: Hardware
---

### Post by MagiSu on 2008-10-23
Hello, guys! I am really having a terrible problem. I installed Intrepid Beta a few days ago. Most of the system works well, while the wireless and ethernet drivers are compiled myself. However, the point is, the integrated Intel 4500mx Graphics Card is NOT recognized by the X System. That is, even I use VESA driver, it stuffed my desktop, fill it up with strange patterns. Does anyone have the same issue? A recompile of xf86-video-intel driver with newest 1.42 version won't help!

(PS: ArchLinux works well when the driver is recompiled)

I REALLY WANT TO MAKE THIS UBUNTU WORK SOON! I HAVE MATLAB FOR LINUX ONLY, NEED TO USE THAT FOR MY HOMEWORK!

---

### Post by n0manarmy on 2008-10-30
I have a T400 with the Intel Series 4 graphics chipset and I didn't see any of the described issues with the release candidate or the full release. I am experiencing issues with the fact that xorg won't detect my intel driver and sets it up as a generic card at 1024x768. The strange thing about that is in 8.04 it found my intel card fine, it just hated the wireless card.

EDIT:
Now it is a long shot but when I first tried to install 8.04 on my T400 it freaked out with graphical problems so I tried the install with safe graphics mode which worked fine. I'm now doing safe graphics mode with 8.10 to see if it will do the same thing (allow the intel drivers to function.)

EDIT2:
Installing 8.10 on my Lenovo with safe graphics mode worked for giving me appropriate resolutions for my display. This is because it's setup as Vesa

---

### Post by menator on 2008-10-30
I am also a thinkpad t400 owner with the intel 4500hd video chipset. I cannot seem to get 1440x900 resolution working either.

---

### Post by menator on 2008-10-30
I tried compiling the latest intel driver to no avail. A lot of new laptops have this chipset. I opted out of the ati card for this laptop to avoid graphics issues and it looks like I'm stuck anyway. Any ideas?

---

### Post by fstonedahl on 2008-11-08
Even though you didn't install the discrete ATI card, you might need to go into the BIOS and disable the switchable graphics option, and set the card type to Integrated only.  Have you tried this?

My T400 has both graphics cards, but I set it up to use the integrated one.  I just followed (and helped edit) the directions here, when installing 8.10.

[http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_(Intrepid_Ibex)_on_a_Thinkpad_T400](http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_(Intrepid_Ibex)_on_a_Thinkpad_T400)

---

