---
title: "Nvidia 195 drivers fail to initialise after every reboot"
date: 2010-05-07
forum: Hardware
---

### Post by JayneDee on 2010-05-07
Hi all,

Well I've recently switched from an ATI HD4870x2 to an Nvidia Geforce 9800 GT for noise reduction, heat reduction and general linux support; which is much better I must say.

First off I removed all the ATI / fglrx items from synaptic, shutdown, swapped my cards and rebooted. The vesa drivers took over as expected and the hardware driver detection tool prompted me to install the Nvidia drivers which I did with no issues. I restarted my PC and everything was okay. 

I started installing some older commercial game ports like Quake which previously did not work (or in the case of Quake 3 froze) and they ran fine. However after purchasing X3: Reunion for linux it told me there was no driver installed.

I took a quick look on the LGP FAQ for X3 and it told me that if I'm on a an x64 distro then it's likely I do not have the compatibility drivers installed. Obviously, with the ubuntu driver tool there was no option for this. So I proceeded to download the latest stable drivers from Nvidia.com, shutdown X, installed the drivers (pressing yes to the 32 bit compatibility drivers) and rebooted X. 

This appeared to work and was great, now I can run pretty much every commercial game port I own that was previously not accessible due to ATI.

However, I rebooted the other day (I leave my machine on for a few days at a time usually) and I was told that X failed to initialise my graphics drivers as "nvidia" was not found. So first thing I did was delete my xorg.conf to see if it would initialise the drivers without the config file (I don't know if this is a silly thing to do, but I'm not an advanced linux user and read that new versions of X don't need it to run in a lot of instances). This didn't resolve the issue.

I rebooted a couple of times, trying to tweak the xorg.conf with no luck. Attempting to start the nvidia X server setup prompted me that the drivers are not loaded and I should run "nvidia-xconfig", which I did, but still nothing.

I also tried booting into a different kernel version (one version prior) but that did not help.

I did a bit of googling and couldn't really find anything that was very similar to my issue, so I decided to try reinstalling the drivers. So i repeated the process and when I started X, magically the drivers were working again. I took a gamble and rebooted yet again, however I found I was looking at the "low graphics mode" prompt and back to square one. So right now each time I boot I am booting into the shell prompt and installing the drivers over again.

I did notice that ldconfig apparently failed to run on each reinstall of the drivers, but I don't recall it appearing on the first install.

My system is:

Mobo: DFI Infinity X48
CPU: Intel Q6600
RAM: 8GB GeIL PC8500
GFX: Asus Geforce 9800GT 1GB
OS: Ubuntu 10.04 x64_x86.

Any help would be very much appreciated, and please bear in mind while I'm not a newbie to computers I am not an advanced linux user. 

Thanks!

---

### Post by JayneDee on 2010-05-08
Bump.

---

### Post by frank8880 on 2010-05-08
i have a similar issue, but now my system won't boot up, here's a link to my thread i mean i have 2, i initially had a problem with the video card performance while playing full screen hd videos but now my problem seems to be like yours, here are the links to my threads:

[http://ubuntuforums.org/showthread.php?t=1476480](http://ubuntuforums.org/showthread.php?t=1476480)

[http://ubuntuforums.org/showthread.php?t=1477195](http://ubuntuforums.org/showthread.php?t=1477195)

---

### Post by JayneDee on 2010-05-09
I can't say I've had any issues once the drivers are initialised, only that they don't like being initialised after a reboot.

---

### Post by JayneDee on 2010-05-10
Bump again.

---

### Post by khelben1979 on 2010-05-10
Did you read the nVidia installation instructions before installing?

---

### Post by JayneDee on 2010-05-10
Unfortunately, the readme link on the driver page is broken and the "howto" install says nothing other than what I did :(

I dug around a bit more on the nvnews forum and there is a suggestion that having the restricted binaries active may cause issues though it doesn't say anything specific.

Will remove everything, reinstall the nvidia drivers and see what happens and report back.

---

### Post by JayneDee on 2010-05-12
Hmm, still not working.

May have to try reinstalling...

---

### Post by fh_scott on 2010-07-15
I'm having the same issue. No resolution yet, although I made things much worse before restoring them to just needing to reinstall the driver after each reboot.

---

