---
title: "ATI 4850/4870 and Ubuntu 8.10"
date: 2008-10-28
forum: Hardware
---

### Post by Darthcolo on 2008-10-28
Hi, anyone had solve the driver problem with ATI 4850 and Ubuntu 8.10? What drivers are working??? HOW!?!?!? Thanks... :confused:

---

### Post by Izek on 2008-10-28
Probably will have to patch it the manual way like everyone else (including me, but this is annoying, and roundabout. So I won't do it.)

[http://www.phoronix.com/forums/showpost.php?p=48886&postcount=10](http://www.phoronix.com/forums/showpost.php?p=48886&postcount=10)

---

### Post by Darthcolo on 2008-10-28
Thanks for the reply...

Can you explain this: 
a) remove all old arch common x* dirs completely
b) create a new common dir, put etc lib opt usr from 8.543 in there the rest just copy to extracted 8-10 dir
c) rename x740 to x710 and x740_64a to x710_64a
d) now you can execute

I don't understand the a) part...

Can you install the drivers from ATI webpage?

---

### Post by Izek on 2008-10-28
Neither do I, I'm not a real linux user.

---

### Post by Darthcolo on 2008-10-28
anyone???

---

### Post by theApokalypsis on 2008-11-03
Hey All,

picked up a 4870 card last week on the move from Nvidia to ATI. Switched to Ubuntu Ibex 8.10 from Mint. So here is how to do it. Only issues are 3d accelerated video playback flickers which ive read ATI is working on for the next release. I will list some possible solutions below as well. The trick I learned from a wiki was that the 8.10 drivers you can manually build fail since the kernel is so new and not supported. You gotta build it for Ubuntu/hardy or Ubuntu/8.04 (not Ubuntu/intrepid or Ubuntu/8.10)!

I had some luck with some open source drivers from a ubuntu developers PPA but still no compiz. After emailing that developer I found out they are still working away at 3d accelerated support. Gotta love the full AMD support in GNU/Linux development and open source 3D specs though! :D



So... grab a .run installer from the amd/ati site.
[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)


navigate to the directory and in the terminal

sudo sh ati-installer-name.run --buildpkg Ubuntu/hardy


this will then build a .deb (you need build essentiall, libc etc for make of course). Then run the deb install (x64 users you need to use the --forceall option). Then after the install is finished run 

sudo aticonfig --initial

this will set up your xorg.conf for use with catalyst. Note: if you add any extra options to the xorg.conf file you need to run

sudo aticonfig --input=/etc/X11/xorg.conf

which will actually make the changes take effect.


good luck! let me know if you have any issues.




ps. about the flickering, you can use VLC player and for the time being switch the video playback to X11 in the preferences. If you use totem you can use

gstreamer-properties

and under the video tab change Video Output Plugin to "X Window System (No Xv)"

---

### Post by Darthcolo on 2008-11-03
So... you get it to work on 8.10?? great! I am still whit 8.04 but I'll try this when I change to 8.10. Thanks men!!

---

### Post by Izek on 2008-11-10
I did what theApokalypsis said, but now I can't enable my driver, and in turn, cannot enable my effects.

So I had to go back to using the new beta driver, which is very choppy and slow at times.

---

### Post by Izek on 2008-11-12
I reported it here in jockey:

[https://bugs.launchpad.net/jockey/+bug/296815](https://bugs.launchpad.net/jockey/+bug/296815)

---

### Post by theApokalypsis on 2008-11-13
> **Izek said:**
> I did what theApokalypsis said, but now I can't enable my driver, and in turn, cannot enable my effects.

So I had to go back to using the new beta driver, which is very choppy and slow at times.
did you try completely removing all the open source drivers? here is what my xorg.conf is set up as... if you decide to try er again hope this may help.

/--------------------------------------------------------
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	Option	    "AIGLX" "on"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "EnableMonitor" "crt1,lvds,tv,tmds1,crt2,tmds2,cv,tmds2i"
	Option	    "XAANoOffscreenPixmaps" "on"
	Option	    "TexturedVideo" "on"
	Option	    "VideoOverlay" "off"
	Option	    "OpenGLOverlay" "off"
	Option	    "Texture2D" "on"
	Option	    "UseFastTLS" "1"
	Option	    "BackingStore" "on"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Group        "Video"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "RENDER" "Enable"
	Option	    "DAMAGE" "Enable"
	Option	    "Composite" "Enable"
EndSection
/--------------------------------------------------------

---

### Post by theApokalypsis on 2008-11-13
Just saw it up, 8.11 Released Today!

[http://ati.amd.com/support/drivers/l...64-radeon.html](http://ati.amd.com/support/drivers/l...64-radeon.html)
[http://ati.amd.com/support/drivers/l...ux-radeon.html](http://ati.amd.com/support/drivers/l...ux-radeon.html)

i will post about the flickering isssue when i get it installed!

:D

---

### Post by Izek on 2008-11-13
>>Delete Post<<

---

### Post by theApokalypsis on 2008-11-13
:( appears flickering accelerated video is still aparrent with 8.11... tried some mixed settings to no avail...

good news is the 8.11 release officially supports Ubuntu, so you can run the stock installer (instead of building debs) :D

---

### Post by Izek on 2008-11-13
And I still get flickering on my screensavers (3D ones)

---

### Post by theApokalypsis on 2008-11-15
from another thread (same post about 8.11)...

> **binbash said:**
> It is not possible to fix it till DRI2 comes, at least for ati. But you can disable flickering at videos with selecting X11 as video output

---

### Post by fatka on 2008-11-23
I was wondering whether updating the kernel requires me to reinstall the drivers again?

Edit:
I installed the latest 8.11 drivers
> $ls Downloads/ati*
Downloads/ati-driver-installer-8-11-x86.x86_64.run

everything went as was mentioned in the release notes. however after the reboot, X failed to find the proper driver and started in 800x600. I logged in to a failsafe terminal and uninstalled the crappy stuff, restored the original xorg.conf and went back to open source drivers. this is a work machine so I can't experiment much.

Hardware: HD4850 from Diamond
> $ lspci |grep ATI
00:00.0 Host bridge: ATI Technologies Inc RD780 Northbridge only dual slot PCI-e_GFX and HT1 K8 part
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:0a.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port F)
This is from my messages,
> $ grep ATI /var/log/messages 
Nov 21 20:58:24 numu kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.
Nov 23 17:32:47 numu kernel: [160209.661099] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Nov 23 17:43:49 numu kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.
Nov 23 17:43:49 numu kernel: [   32.303973] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Nov 23 17:56:00 numu kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.

and I was considering to buy ATI for my personal desktop! hopefully I can sort this out before the purchase

---

### Post by Z4ndX on 2008-11-28
Hi... can any one confirm that the drivers work ? .. 

Thinking of purchaseing the HD4850 and would be nice if it would work with no ssues on Ubuntu.

---

### Post by Hadraniel on 2008-11-28
I use the HD4850 scince ~ two weeks with a Radeon HD4850 and the fglrx-drivers which are bundled with Ubuntu 8.10.

Besides from the video flickering issue (which can be workarounded by turning off Compiz Eyecandy or setting VLC Video-Output to X11), everything's just fine.

For setup I simply used the ati-config tool and added a few lines which I gathered here in the forums. Did not tweak or experiment any more, just one shot and running. That was much better than expected and I don't intend to mess anything up now for some senseless 'tuning'.

Don't know if the driver supports any energy saving functions (ATI PowerPlay(tm)), though. I hope, it does. My Gigabyte HD4850 is passive cooled with huge sinks and exceeds 110°C when under full load and *not* being cooled by some fan. 2D operation only is <50° (WinXP).


Also, I still have a dual screen setup enabled from my previous (on-board 780G HD3200), but not second screen attached yet (waiting for TFT). But it looks like DualScreen also will be just fine.

---

### Post by Ubuntiac on 2008-11-29
Same here.

I didn't do any fancy compiling / xorg.conf tweaking / manual installing to get my HD 4850 running on 8.10. I think the fanciest I got was to install the drivers from envyng rather than jockey. In otherwords:

apt-get install envyng

run envy, choose Install ATI driver and accept the recommended version.

Admittedly my video playback kinda seems to suck (laggy), but everything else works great.

---

### Post by Hadraniel on 2008-12-01
After a recent kernel upgrade (2.6.26-7-server to 2.6.26-9-server), my fglrx-drivers were trashed due to the missing, newly built dri-kernel-module.

I tried to fix it by switching to the RadeonHD driver, which is said to support the HD4xxx-series. Unfortunately, I got nothing than a white blank screen.

The third ATI-Driver (Ati-Video) does not support RV770 but older ATI GPU chipsets, so I did not try it out.


Finally, I used envyng to reinstall the the fglrx-drivers - including a working kernel module.
So I agree to Ubuntiac: anybody who does not want to mess around should go with envyng. It's KISS fire & forget.

---

### Post by 00arthuryu on 2008-12-01
I first installed mine with the drivers from 8.10 restricted driver manager, these were incredibly slow... especially on compiz
switching windows by turning the cube, it just simply doesn't turn...
Then i tried installing the drivers from the ati website by running the default installer. It worked, but it is still ridiculusly slow.

Do not try and run any sort of 3D with compiz on, as it will crash X
I'm also not too sure if it is just me or not

Anyone else getting this performance issue? and/or howto solve it? :confused:

---

### Post by Hadraniel on 2008-12-01
> **00arthuryu said:**
> I first installed mine with the drivers from 8.10 restricted driver manager, these were incredibly slow... 

Check your /var/log/Xorg.0.log if the fglrx-driver has all the kernel modules it needs. I bet (at least) the dri is missing.

Scince to my experience the kernel module autobuilder is somewhat buggy during fglrx-setup, I'd heavily recommend the use of envyng. Did the job on my PC.

Also, you might wanna study these threads
[list]
[*][compiz is running really slow](http://ubuntuforums.org/showthread.php?t=990479)
[*][ATI driver stops working after kernel update](http://ubuntuforums.org/showthread.php?t=996227)
[*][The Great Desktop Effects FAQ of 2008](http://ubuntuforums.org/showthread.php?t=809695)
[/list]

good luck!

---

### Post by 00arthuryu on 2008-12-01
Thanks for the reply, but it seems that envy just installed the same graphic drivers that i have had previously =/

Granted i'm using 64bit and using bigdesktop, but even a X1950Pro could do better! :confused: 
I guess all I can do is wait for the drivers to mature =/ *sigh*

---

### Post by Hadraniel on 2008-12-02
> **00arthuryu said:**
> Thanks for the reply, but it seems that envy just installed the same graphic drivers that i have had previously =/Sure it did, but dit you notice the compilation of a kernel module during installation?
Have you checked the Xorg.log for error messages?

Try purging the fglrx-drivers (dpkg --purge fglrx) from your system and run envy textmode installation afterwards.

> Granted i'm using 64bit and using bigdesktop, but even a X1950Pro could do better! :confused: 
I guess all I can do is wait for the drivers to mature =/ *sigh*4850 does wirj fine on my 64bit Ubuntu, with 3800x1920 screen (2xTFT).

---

### Post by zaine_ridling on 2008-12-06
> **Ubuntiac said:**
> Same here.
- apt-get install envyng
- run envy, choose Install ATI driver and accept the recommended version.


Yet another solution that didn't work on my ATI 4850. Arrrrrrggghhh!! :mad: 
Thanks anyway.

---

### Post by 00arthuryu on 2008-12-06
Actually i got mine to work now, its because i've upgraded from a Nvidia card 7900GS and somehow that interfered with the new ATI drivers. So i wiped the system and installed a fresh copy and then the ATI drivers and it worked!

Hopefully it will be of some use to someone
cheers
:popcorn:

PS. you have a weird resolution 1900x1920 monitors??

---

### Post by fatka on 2009-01-20
this did the trick for me,
```

sh ./ati-driver-installer-8-12-x86.x86_64.run --listpkg
...

Package Maintainer(s): Mario Limonciello <superm1@gmail.com>
                      Aric Cyr <aric.cyr@gmail.com>
Status: *UNVERIFIED*
Ubuntu Packages:
	Ubuntu/7.10
	Ubuntu/8.04
	Ubuntu/8.10
	Ubuntu/9.04
	Ubuntu/gutsy
	Ubuntu/hardy
	Ubuntu/intrepid
	Ubuntu/jaunty
	Ubuntu/source

For example, to build a Debian Etch package, run the following:
% ./ati-driver-installer-<version>-<architecture>.run --buildpkg Debian/etch

```

now build as per your version of Ubuntu.
However a word of warning, the dependencies are a little borked up. as in it depends on libstdc++5 rather than 6, and you might want to install compat-* libraries rather than downgrade. Also video playback might be a little choppy, specially with VLC.
YMMV ofc :p
God Luck

---

### Post by keypox on 2009-01-25
man this sucks still no proper 48x0 support.   This is BS.  I was running 8.10 but it sucks for the videos to look like crap.  Even with Compiz disabled they still didnt look as good as in vista.  

Hopefully new ati drivers come soon with some maturity.

---

### Post by Izek on 2009-01-25
> **keypox said:**
> man this sucks still no proper 48x0 support.   This is BS.  I was running 8.10 but it sucks for the videos to look like crap.  Even with Compiz disabled they still didnt look as good as in vista.  

Hopefully new ati drivers come soon with some maturity.

We'll see about that when Jaunty comes out. According to some, jaunty has better ATI interaction.

Also, [read this](http://ubuntuforums.org/showthread.php?t=1025627).

---

