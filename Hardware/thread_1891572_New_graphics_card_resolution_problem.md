---
title: "New graphics card resolution problem"
date: 2011-12-05
forum: Hardware
---

### Post by nookawarra on 2011-12-05
A couple of weeks ago my GPU died and I replaced:( it with a GeForce 450 that was very well priced. My old configuration would not drive it so after some searching I installed Nvidia driver 290.10. Still had problems until I removed the Nvidia drivers from the repositories. I can now start the machine without re-installing the driver each time but it always starts at the wrong resolution. I have posted my xorg.conf file which says it should be 1920x1080 but it always starts at 1280x1024.
I have also posted my Xorg.0.log file and it looks as though it changes to the lower resolution late in the proccess. I have tried changing the Grub commands from 'quiet splash' to 'nomodeset' without success.
System>Administration>Hardware Drivers reports that no proprietary drivers are in use. However System>Preferences>NVIDIA X Server Settings shows all the settings in use.
I am using 10.04 and it is up to date.
I have installed Kubuntu on another partition and it does not have the same problem although I have not installed any Nvidia drivers.
Not a huge problem as I can re-set the resolution after boot but it is annoying that I can't find a solution. Help would be much appreciated.

---

### Post by pqwoerituytrueiwoq on 2011-12-05
does it have right resolution when the login screen is up?
post output of this:
sudo hwinfo --framebuffer
pick the highest one one the right aspect ration that does not exceed your screens with/height in my case it is 1280x800-24

be sure you have v86d installed
from my menu.lst file:
defoptions=quiet splash nomodeset video=uvesafb:mode_option=1280x800-24,mtrr=3,scroll=ywrap

---

### Post by nookawarra on 2011-12-05
Thanks. I have posted the output from hwinfo but none of the resolutions match my aspect ratio. Is that a basic problem? The old card worked fine with this screen.
I have installed v86d and it created /boot/initrd.img-2.6.32-36-generic. Same problem on reboot.
The logon screen does appear to have the correct resolution.
I tried editing the Grub settings on startup but did not include all of your line because I thought the uvesa instructino might conflict with Nvidia. I used
defoptions=quiet splash nomodeset mode_option=1920x1080-24

Perhaps this is not correct?

---

### Post by nookawarra on 2011-12-06
Hi pqwoerituytrueiwoq

I realised that it was pretty silly to not use all of your defoptions so I rebooted and put in your complete line (with my native resolution) and it made no difference.:(

---

### Post by nookawarra on 2011-12-06
Success!!!:D

I played around here [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) and thought I had really broken something. Only way I could boot was through the recovery mode at 800x600.
Then I uninstalled and reinstalled the Nvidia driver - it didn't work the first time but then I blacklisted the open source drivers and presto! It has now booted twice directly into 1920x1080. However hwinfo still does not show this mode (I guess this doesn't matter if it works anyway).
Many thanks for your help - just having someone take an interest made me really work on it.

---

### Post by pqwoerituytrueiwoq on 2011-12-06
as long as it works...
are you using the hdmi cable or the dvi cable?
i had sound issues with the dvi i had to blacklist the hdmi sound driver (programs did not know which output to use)

---

### Post by nookawarra on 2011-12-08
I am using DVI - never tried HDMI but I should. My sound system had not been reconnected after changing the graphics card so I did it today and it all works. Thanks again for the assistance.

---

