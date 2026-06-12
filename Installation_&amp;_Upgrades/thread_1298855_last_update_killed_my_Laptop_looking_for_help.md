---
title: "last update killed my Laptop looking for help"
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by slick666 on 2009-10-23
Dear Forum,

    I must say that this is a first in my expierence. I have a Macbook (1, 1) with Ubuntu 9.04 on it. I recently got a bunch up updates and like usual I had the system update. I have done this on at least two other system earlier that day so it was no surprise and I didn't pay it much attention this time. After completing the update the system does not boot completely.

The system will hang either
* At the login screen
* Just past login it will, it may play the login sound or not and it will render the two bars at the top and bottom of the screen but thats it.

I've gone back and tried booting kernels 15, 14, 13, and 11 but all have the same result. I don't think the issue was the upgraded Kernel or else the other kernels would have booted. I can't recall at this point what exactly was updated besides the kernel and I'm feeling a little desperate. I'm looking for any insight that would help diagnose the issue or a process that I could restore the system.

Thanks in advance

---

### Post by BoredOutOfMyMind on 2009-10-23
Same result here and it is the video drivers... Not a solution to Bug#1 to break Ubuntu on the same day as Win7 is released!

---

### Post by slick666 on 2009-10-23
My system is dual boot so I can get access to the hard drive and mod or update the FS but I would have to know what to do.

---

### Post by ducky12432 on 2009-10-23
Yea same thing here any help at all would be appreciated.

---

### Post by slick666 on 2009-10-24
I understand that the issue is with the video driver. I've gone in under the recovery console and looked into xorg but I don't see how I can change the driver. Any help appreciated.

---

### Post by beastrace91 on 2009-10-24
The intel video drivers are open source & part of the kernel. You cannot upgrade them. Have you seen the [Jaunty Performance for Intel HOWTO](http://ubuntuforums.org/showthread.php?t=1130582)? Its a sticky in the multimedia section.

That being said I would recommend giving Karmic a go (it releases soon anyways) one of the big new things it sports is better intel card support. If you do not have much data on your Ubuntu partition I would recommend doing a clean install of 9.10 - as upgrades can be messy.

Regards,
~Jeff

---

### Post by slick666 on 2009-10-26
Since my home is on a different partition (highly recommend people do that I ended up installing 9.04 again. After completing the installation I upgraded 246 MBs. I rebooted and had no problems. I backed up my installed packaged using the command
```
dpkg –get-selections > installed-software.log
```

I then restored it using the following commands
```
dpkg –set-selections < installed-software.log
apt-get dselect-upgrade
```

This installed another 1.2 Gigs of software including all the old kernel which I know I don't need but I wanted to replicate my old setup. This not only didn't have any problem but my graphics acceleration that I had lost on the 9.04 install (and yes it was a fresh install) was restored. I don't know what to attribute the final problem to but I can't repeat it. I'll be upgraded to Karmic in just a few days anyway.

---

