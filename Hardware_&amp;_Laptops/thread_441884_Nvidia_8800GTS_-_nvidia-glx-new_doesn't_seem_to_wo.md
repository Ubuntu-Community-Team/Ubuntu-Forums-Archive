---
title: "Nvidia 8800GTS - nvidia-glx-new doesn't seem to work"
date: 2007-05-13
forum: Hardware &amp; Laptops
---

### Post by atari05 on 2007-05-13
Hello all!

I have an 8800gts and I'm trying to get the nvidia binaries to work and I'm having some issue. The "nv" modules works fine, its just the darn nvidia-glx-new driver that doesn't seem to work. In ubuntu, I get dropped to a text login, followed by a ncurse based screen that says X can't start. In kubuntu, I get just a black screen. Mind you, this is after running nvidia-glx-config enable. I have tried to go into the restricted file and add "nv" so it doesn't load, I have tried adding it to "blacklist" for giggles. Still I get nothing. I had made a quick post in general while trying to deduce what the issue might be and the link is below. There you will find my Xlog, xorg.conf and dmesg output. 


Oh also, I "installed" the driver just by opening Synaptic and selecting the glx-new package as the RMM tool loads the 96(?) based driver, from which I understand does not support 8800's at all.

Any help is GREATLY appreciated cause I have NO CLUE as why its not working, when I get the text login, I login, do a lsmod and see the nivdia module loaded and no "nv" is referenced.

[http://ubuntuforums.org/showthread.php?t=434389](http://ubuntuforums.org/showthread.php?t=434389)

**EDIT**
a quick note also, I have searched the forums already and tried the various how-tos and "what I did's" and still no luck as all of them revolve around the same process in which I followed (install driver, blacklist the nv module, reboot and it should work). I know I can most likely download and install striaght from nvidia but I don't want to do that as that with package based distros, as soon as you deviate the likely hood you run into an issue later due to updating increases.

---

### Post by Dekunuts on 2007-05-13
if you think installing the drivers from the nvidia website will help, you can get those and make a .deb out of them. That way they will be listed in synaptec. There are plenty of guides around on how to do that. 

Also, if you type sudo dpkg-reconfigure xserver-xorg on the command line, you can configure your graphic card again using the default driver, thus giving you access to a graphical desktop environment. type sudo reboot now to restart the pc after you have reconfigured the data.

---

### Post by atari05 on 2007-05-13
I could do that, but once again, I want to stay inline with Ubuntu repo's so when I update via the update manager its less likely to have issues after, or during an update.

Basicaly, I will download the nvid driver from the site if I can't come up with anything but I was hoping that someone here might have had the same issue or could supply some alternative thinking to my issue at hand

---

### Post by atari05 on 2007-05-14
bumping for good measure

---

### Post by defri on 2007-05-14
I have same problem like you. But can you open the xorg.conf and search the section device. Is the driver show  you the driver that you get ? "nv" or "nvidia"? and find the text about your graphic card! Is your graphic card known correctly? If your graphic card known correctly but the driver still "nv", try to change it manually to "nvidia". My problem solve with this way. I hope it success with you!

---

### Post by atari05 on 2007-05-15
--- ISSUE RESOLVED --

Symptoms:
     Xserver crashes after installing the "nvidia-glx-new" package to support the Nvidia 8800 series of cards (gts,gtx)


Resolution:
    after digging in my log I foudn that the libwfb module is not present. After some searching I cam across the below URL that explains how to hack around this until its included

[https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/98641](https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/98641)


I hope this helps anyone in the future!

---

