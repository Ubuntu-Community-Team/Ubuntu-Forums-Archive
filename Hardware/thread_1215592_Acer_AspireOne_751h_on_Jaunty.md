---
title: "Acer AspireOne 751h on Jaunty"
date: 2009-07-17
forum: Hardware
---

### Post by divan0 on 2009-07-17
AA1 751h is an 11 inch netbook with great design and Intel Atom Z520 1.33 CPU inside, 1Gb RAM and 160 GB HDD. It's based on Intel Poulsbo (actually US15W) chipset, with GMA500 graphic chip - it has basic 3D and advanced hardware video decoding capabilities. Keyboard is big for netbooks - 99% full-sized laptop keyboard, screen is great and bright and the 6-cell battery really gives a 7-8 hours to this netbook.
[IMG]http://notik.if.ua/images/products/b/253_1.jpg[/IMG]
I've installed Ubuntu Jaunty via the netboot, and this stage doesn't require much attention here, all went smoothly.

Next, one-by-one, using **2.6.28** default kernel:
0) **Good things**. Almost everything worked out-of-the box:

[LIST]
[*]Sound - with default Jaunty's ALSA 1.0.18rc3 sound works well. It has the Realtec ALC272 chipset and uses HDA Intel driver(hda_intel).
[*]WI-FI - works great, without any problems discovered. ath5k driver is used. Leds seems not to work, but I saw it mentioned in 2.6.30 patch.
[*]Bluetooth - works great.
[*]HDD. Here is the hdparm test:
[*][B]# hdparm -tT /dev/sda1
/dev/sda1:
 Timing cached reads:   896 MB in  2.00 seconds = 447.31 MB/sec
 Timing buffered disk reads:  180 MB in  3.01 seconds =  59.89 MB/sec[/B]
[*]CardReader - I tested it only on SD-HC card, works perfectly.
[*]Hibernate/Sleep Mode - works out-of-the-box, no problems with restore - sound,net,video works as before.
[*]Touchpad and USB devices - no problems.
[*]Total boot time is about 40 seconds. Pretty nice for default installation.
[/LIST]
1) **Bad things.**

1. X.Org - first thing you see is distorted and slow Xorg. it uses default driver(vesa, I guess) and Poulsbo driver should be installed separately. Fortunately, it's easy:
[LIST]
[*]- add the following line at the end of** /etc/apt/sources.list**: **deb [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main **
[*]- execute the following commands from command line:
[*]**sudo gpg &#8211;keyserver keyserver.ubuntu.com &#8211;recv 0×99d6b21cc6598a30; sudo apt-get update;**
[*]**sudo apt-get install xserver-xorg-video-psb**
[*]I also installed [libgl1-mesa-dri-psb_0.25-0ubuntu1~810um1.1_i386.deb]("http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu/pool/main/libg/libgl1-mesa-dri-psb/libgl1-mesa-dri-psb_0.25-0ubuntu1%7E810um1.1_i386.deb") from [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu/pool/main/libg/libgl1-mesa-dri-psb/](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu/pool/main/libg/libgl1-mesa-dri-psb/) manually, cause didn't find it in repository Packages list.
[*]Restart the system(or restart X and 'modprobe psb' before) and it nicely will bring 1366x768 with basic acceleration.
[*]Here is glxgears output:
[*][B]$ glxgears 
1153 frames in 5.0 seconds = 230.592 FPS
1171 frames in 5.0 seconds = 234.018 FPS
1165 frames in 5.0 seconds = 232.928 FPS
1154 frames in 5.0 seconds = 230.570 FPS[/B]
[/LIST]
2. I noticed hangs a few times - mouse was moving, but all the system freezes. My guess is about CPU temperature - I installed sensors applet to check and I'm almost sure that this freezes are connected to the CPU temperature raising. After googling, I saw the acerhdf module(which responsible for fan and temperature control for Acer Laptops) was added in 2.6.30, and installed the kernel from Karmic Koala Alpha, which is 2.6.31-rc3. I did a stress CPU load and saw the temperature raising, but system works well. Anyway, I can't be sure, cause the other possible reason is the psb-driver, which has proprietary binary code and could be the problem as well. But the psb kernel module doesn't compile on kernels > 2.6.28 yet.
**UPD: I've made a patch to allow psb kernel module work with 2.6.31-rc3, but the system still hangs, and seems the problem in the PSB X.Org module :(**

So, I will try to make it work and hope it will not take too long to wait until the GMA500 will be supported at 100%.
I don't need a 3d on the netbook, but the web-browsing speed is slow.. And it's definitely the problem of video driver, not a CPU. Default mplayer(with -vo xv and framedrop=soft) plays regular divx/mpeg4 movies very well, and I'm able to play even 720p HD clips(not movies) - and this is without hardware acceleration enabled. As for the last, I followed this steps:
[http://gwenole.beauchesne.info/en/blog/2008/12/24/mplayer_with_va_api_acceleration](http://gwenole.beauchesne.info/en/blog/2008/12/24/mplayer_with_va_api_acceleration)
but it doesn't work for me yet - the newly built mplayer fails on -vo va. Will try more a little bit later.

A few most relevant logs attached, maybe it will help someone.

---

### Post by divan0 on 2009-07-18
Attached psb-kernel-source patch and X.org to allow psb kernel module works in 2.6.31-rc3 kernel.

---

### Post by Metoshade on 2009-07-26
Thank you for working on the Poulsbo driver!

I have an MSI X320 (Atom Z530 and GMA500) which doesn't run smooth under Ubuntu at the moment. Hopefully your work will help me out as well!

If there is anything I can do, let me know.

---

### Post by raphoun on 2009-07-28
Thanks for your topic, I hope the poulsbo driver will be stable soon!

---

### Post by lucazade on 2009-07-29
any chance to make a ppa repository for karmic?
or how to compile for 2.6.31?

thanks
Luca

---

### Post by sammyboy405 on 2009-08-12
[http://ubuntuforums.org/showthread.php?t=1229345](http://ubuntuforums.org/showthread.php?t=1229345)

Check this thread and guide out it might help you out in tweaking the video setting on the GMA500.

Ive gone though several hoops to see what works and what doesn't.  With 3d Enabled the Freezes are from some conflict with USB devices best we have been able to tell. 

So if everyone can join up who has netbooks with GMA500's on them maybe between all of us we can get something to work.

---

### Post by divan0 on 2009-08-12
**[lucazade]("http://ubuntuforums.org/member.php?u=242850")**, you can try my patch in second message of this thread to build driver on 2.6.31.

**[sammyboy405]("http://ubuntuforums.org/member.php?u=663333")**, great contribution, thanks! Are that freezes really was connected to USB devices? I had only mouse plugged in. 
That laptop was a present, so I cannot check your instructions right now, but once I'll get it again, I write the experience with your configuration applied.

---

### Post by tjwallace on 2009-09-18
divan0,

Can you help me apply your patch?  Just a couple quick steps would be great!

Thanks!

---

### Post by crgutierrez on 2009-09-26
Does your front mic (next to the webacm) work? it does not in my case. Best. carlos

---

### Post by crgutierrez on 2009-09-26
neither does the wifi work for me.......

---

### Post by JeremyRuhland on 2009-09-26
Thank you, this really helped. 
The crashes are annoying and always seem to happen when I finish downloading things in firefox, but a few times the computer was just sitting there doing nothing. Does anyone know if it's somehow connected to crashes on wakeup? Several times I've had the screen go black with a string of green dots along the top, and I've had to restart.

---

### Post by seannon on 2009-09-27
I got the first one available in my area, as soon as it was released... the freezing issue is NOT just with Ubuntu... mine has been to the service center three times now, finally it has stopped crashing in Windows... but it continues to do so under Linux... and this is the "The screen stops but the mouse is still active..." this affects it in BOTH OS's and was even doing it when running with no HDD at all, just an SD card... Acer updated the BIOS firmware on mine, and changed the HDD the last time, so there could be an issue of it being kinda picky with drives as well... I just got a D250 last week, and it seems to be doing great :D running Karmic on it now...

---

### Post by nummer on 2009-11-29
Cheers, anad thanks for a great effort with these gma500 drivers. I got a asus eepc 1101, running both 9.10 and 9.04. Been struggeling with the drivers for gma500 for some time now.

I have tried most of the suggestions but with no real luck. Seems like I have to build the psb module my self. But the patch mentioned here [http://swiss.ubuntuforums.org/showpost.php?p=7773647&postcount=13 ]("http://swiss.ubuntuforums.org/showpost.php?p=7773647&postcount=13") cannot be downloaded? seems like I don't have access to the files??

---

