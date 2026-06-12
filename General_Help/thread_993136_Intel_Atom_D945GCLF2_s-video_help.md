---
title: "Intel Atom D945GCLF2 s-video help"
date: 2008-11-25
forum: General Help
---

### Post by j_blue on 2008-11-25
I just purchased a D945GCLF2 board and installed the 32 bit version of Mythbuntu 8.10. The system works properly using a monitor but TV-1 out doesn't work properly

The s-video out (TV-1) produces a picture but the screen just keeps rolling. The TV won't sync the picture. I've tried using xrandr to set different resolutions and scan rates but nothing has worked. I've tried this on a monitor with s-video input and on a tv and neither of them work

Any suggestions?

---

### Post by jdusablon on 2008-12-07
Bump, if only to report same problem. Anyone?

---

### Post by hardyn on 2008-12-07
are you using the correct ntsc or pal?

I have the same board, but have not tried the svideo, actually wasn't aware it had one until you mentioned it :P

---

### Post by azazell on 2008-12-08
the xorg drivers have a problem handling the TV output of this card, please look here: [https://bugs.freedesktop.org/show_bug.cgi?id=17776](https://bugs.freedesktop.org/show_bug.cgi?id=17776)

---

### Post by j_blue on 2008-12-16
I have tried all of the settings such as ntcs and it doesn't help. Also have tried downloading and compiling the newest drivers and still doesn't help.

I guess that we need to wait for Intel to updated the driver. See buglist as mentioned above.

If it doesn't get fixed soon might have to switch to a different OS. Don't like that idea.

---

### Post by halok on 2009-03-06
> **azazell said:**
> the xorg drivers have a problem handling the TV output of this card, please look here: [https://bugs.freedesktop.org/show_bug.cgi?id=17776](https://bugs.freedesktop.org/show_bug.cgi?id=17776)

From reading the above link it looks as though the problem is fixed in Jaunty, i'm running jaunty and i compared my Xorg.0.log file to the one mentioned in the fix and it is showing that my version of the intel driver is the same. I'm going to try tonight when i get home from work will post back how I go.

---

### Post by mattsimis on 2009-03-08
Just tried this with the latest Jaunty build (March 8th x86). Used the Live CD (though obviously booted via USB due to Jaunty CD size bug) functionality. It sadly still doesnt work, boot screens work, when it gets to desktop the TV Screen cannot sync and is all over the place. I tried NTSC, PAL and Secam on the TV (incar, VW Phaeton OEM head unit over SVideo).

I dont have the luxury of switching to VGA on this PC as its integrated in a Car, so I couldnt do anything to troubleshoot, though it was likely pointless anyway. Shame.

---

### Post by halok on 2009-03-08
Yeah i got the same result too, disappointing. I ended up putting a different motherboard into the system for now.

---

### Post by peioazkarate on 2009-03-13
Wang Zhenyu from Intel has written a patch to solve the bug on TV Out for this board. I will try this patch in my D945GCLF2 in a few days. 
Read about it here: 
[http://bugs.freedesktop.org/show_bug.cgi?id=17776](http://bugs.freedesktop.org/show_bug.cgi?id=17776)

Peio

---

### Post by fzzz on 2009-03-20
I built a DEB file with this patch for 8.10 and the D945GCLF2  board.  Also have a working xorg.conf.  Email if interested or even better, if you know of a place to upload it to.

---

### Post by mattsimis on 2009-03-24
Definately interested in this! Dunno about the easiest online sharing, maybe: [http://www.mediafire.com/](http://www.mediafire.com/) ?

---

### Post by fzzz on 2009-03-25
I put xorg.txt (need to rename to xorg.conf) and 2 deb files for Ubuntu 8.10, i386 at

xorg.txt [http://www.mediafire.com/download.php?rdbdzqyzkuj](http://www.mediafire.com/download.php?rdbdzqyzkuj)
dbg deb  [http://www.mediafire.com/download.php?ozfi3t4xkz4](http://www.mediafire.com/download.php?ozfi3t4xkz4)
deb      [http://www.mediafire.com/download.php?uzyzfqdnmy4](http://www.mediafire.com/download.php?uzyzfqdnmy4)

Drop me an email if you have trouble downloading the files and I can email them in return.

---

### Post by mattsimis on 2009-03-25
> **fzzz said:**
> I put xorg.txt (need to rename to xorg.conf) and 2 deb files for Ubuntu 8.10, i386 at

xorg.txt [http://www.mediafire.com/download.php?rdbdzqyzkuj](http://www.mediafire.com/download.php?rdbdzqyzkuj)
dbg deb  [http://www.mediafire.com/download.php?ozfi3t4xkz4](http://www.mediafire.com/download.php?ozfi3t4xkz4)
deb      [http://www.mediafire.com/download.php?uzyzfqdnmy4](http://www.mediafire.com/download.php?uzyzfqdnmy4)

Drop me an email if you have trouble downloading the files and I can email them in return.

Any chance of a 9.04 (Alpha6) build? :P  I completely overlooked the fact you stated 8.10 and just installed the latest!

EDIT: I reinstalled 8.10, installing the Debs above and the Xorg file gave me a blinking cursor on a black screen on reboot, on both TV and VGA. Wouldnt let me switch to another session either. I also found Mythbuntu 8.10 doesnt have power management installed so couldnt set the PC to Hibernate when power switch is pressed.

As the PC is integrated in a car (I have to have car running and hooked up to monitor to do all this, really messy), hibernate/power management + Svideo are a must. 
9.04 on the otherhand seemed to have all the APM stuff working but no progress on the svideo problem.

---

### Post by fzzz on 2009-03-27
I've been getting feedback that the driver and xorg.conf have worked for several others.  Note it is for i386, not 64 bit.  I had to edit a couple paths in the original version of the xorg.conf (in the Files section) to get it to work for me.  If there is any problem parsing the conf file my system pops up a small dialog (on the monitor only, not on the TV) with some info about what is wrong and waits till its resolved.  I also have to have the monitor and/or TV turned on BEFORE powering up the computer.  Otherwise I think all I get is the monitor as no TV was detected?  I'm not sure if changing a line in the monitor section to "disable" "true" would prevent that or not.

BTW, the patch itself isn't mine, I have to give credit to Wang Zhenyu ([https://bugs.freedesktop.org/show_bug.cgi?id=17776](https://bugs.freedesktop.org/show_bug.cgi?id=17776)).  I just built a DEB file to be able to install it on a system with no net access.

As for 9.x, doubtful.  The only computer I am running this on has no internet access so it will probably run exactly what it has for some time.  Its not hard to build a DEB if someone else wanted to though.

> **mattsimis said:**
> Any chance of a 9.04 (Alpha6) build? :P  I completely overlooked the fact you stated 8.10 and just installed the latest!

EDIT: I reinstalled 8.10, installing the Debs above and the Xorg file gave me a blinking cursor on a black screen on reboot, on both TV and VGA. Wouldnt let me switch to another session either. I also found Mythbuntu 8.10 doesnt have power management installed so couldnt set the PC to Hibernate when power switch is pressed.

As the PC is integrated in a car (I have to have car running and hooked up to monitor to do all this, really messy), hibernate/power management + Svideo are a must. 
9.04 on the otherhand seemed to have all the APM stuff working but no progress on the svideo problem.

---

### Post by peioazkarate on 2009-03-30
Because I see the Intel's guys are working on this driver, Instead of apply the patch made by Wang, I solved the problems using the version 2.7-rc1 of the xf86-video-intel. 
Now the s-video out works great!! on my Philips TV, 29"CRT.

How-to:

1) Install with Synaptic (apt-get if you prefer) packages; autoconf, automake, libtool, hwdata, xorg-dev, xorg-docs, libdrm-dev, libgl1-mesa-dev, libglu1-mesa-dev.

2) Download and extract xf86-video-intel version 2.7-rc1 driver and drm version 2.4.5 library.
[http://cgit.freedesktop.org/xorg/driver/xf86-video-intel/](http://cgit.freedesktop.org/xorg/driver/xf86-video-intel/)
[https://launchpad.net/ubuntu/+source/libdrm/2.4.5-0ubuntu2](https://launchpad.net/ubuntu/+source/libdrm/2.4.5-0ubuntu2) 

3) Compile drm library
3.0 cd to your drm directory
3.1 $ ./configure --prefix=/usr
3.2 Edit the "libtool" file and comment 4 lines around the "...directory not ending...." text (if construction that avoids installing on /usr/lib).
3.3 $ sudo make install
You'll see the drm version 2.4.5 library installed on /usr/lib.

4) Compile xf86-video-intel driver
4.0 cd to your xf86-video-intel directory
4.1 $ $ ./autogen.sh --prefix=/usr
4.2 Install or reinstall mesa-common-dev package
    $ sudo apt-get --reinstall install mesa-common-dev
4.3 $ sudo make 
4.4 $ sudo make install

Peio

---

### Post by mattsimis on 2009-03-30
Havent tried your suggestion yet, but thanks for posting. I lot more people than have replied are waiting on this fix!

---

### Post by beowulf573 on 2009-03-30
Thanks for posting the deb files, I built a pc to run Boxee with this board over the weekend and your files saved the day.

I noticed xrandr listed quite a few modes but only a few actually would sync up for me.  I was able to find one that worked reliably so I'm good to go, but I'm curious if other folks ran into the same issue.

---

### Post by nazarener on 2009-03-31
thanks a lot peioazkarate.

i was trying to fix it with the advice from fzzz. but somehow i couldnt get the intel package compiled, didnt know i need the drm library and other stuff. however works like a charm now.

---

### Post by dainsane1 on 2009-04-10
greetings thanks for the deb files 

just have one issue. i get an error when i try to install them. 

"error: dependency is not satisfiable: libpciaccess0"

so i figured no prob i just have to drop it in and i will be fine
no luck package is there but i still get the error 

perhaps i'm daft and missing something? 

just double click the deb file right?


the other method i got as far as installing the packages but then am ?????? when it comes to compiling things have never had Make work successfully for me.

---

### Post by MikeInParadise on 2009-04-15
> **peioazkarate said:**
> Because I see the Intel's guys are working on this driver, Instead of apply the patch made by Wang, I solved the problems using the version 2.7-rc1 of the xf86-video-intel. 
Now the s-video out works great!! on my Philips TV, 29"CRT.

How-to:

1) Install with Synaptic (apt-get if you prefer) packages; autoconf, automake, libtool, hwdata, xorg-dev, xorg-docs, libdrm-dev, libgl1-mesa-dev, libglu1-mesa-dev.

2) Download and extract xf86-video-intel version 2.7-rc1 driver and drm version 2.4.5 library.
[http://cgit.freedesktop.org/xorg/driver/xf86-video-intel/](http://cgit.freedesktop.org/xorg/driver/xf86-video-intel/)
[https://launchpad.net/ubuntu/+source/libdrm/2.4.5-0ubuntu2](https://launchpad.net/ubuntu/+source/libdrm/2.4.5-0ubuntu2) 

3) Compile drm library
3.0 cd to your drm directory
3.1 $ ./configure --prefix=/usr
3.2 Edit the "libtool" file and comment 4 lines around the "...directory not ending...." text (if construction that avoids installing on /usr/lib).
3.3 $ sudo make install
You'll see the drm version 2.4.5 library installed on /usr/lib.

4) Compile xf86-video-intel driver
4.0 cd to your xf86-video-intel directory
4.1 $ $ ./autogen.sh --prefix=/usr
4.2 Install or reinstall mesa-common-dev package
    $ sudo apt-get --reinstall install mesa-common-dev
4.3 $ sudo make 
4.4 $ sudo make install

Peio

Thank you so much for this...Even though I had no idea what I was doing I followed the instructions after downloading the Archive Manager to unpack the downloads and then followed the instructions and after the first boot I started getting something on the SVideo even though the Sync was out..

I replaced the /etc/X11/xorg.conf with the one below and rebooted again ....

> **fzzz said:**
> I put xorg.txt (need to rename to xorg.conf) and 2 deb files for Ubuntu 8.10, i386 at

xorg.txt [http://www.mediafire.com/download.php?rdbdzqyzkuj](http://www.mediafire.com/download.php?rdbdzqyzkuj)
dbg deb  [http://www.mediafire.com/download.php?ozfi3t4xkz4](http://www.mediafire.com/download.php?ozfi3t4xkz4)
deb      [http://www.mediafire.com/download.php?uzyzfqdnmy4](http://www.mediafire.com/download.php?uzyzfqdnmy4)

Drop me an email if you have trouble downloading the files and I can email them in return.

And Bob's your Uncle I have SVideo out.

[IMG]http://lh6.ggpht.com/_dQL03Ks5mSQ/SeZBQorNWaI/AAAAAAAABWw/jSCgGi_1W0w/s144/2009_04_15-MythBuntu-SvideoOK-OP01.jpg[/IMG]

I am using my Video Camcorder for testing SVideo out before moving the PC to the family room.

The days of my Windows Media Center Computer are numbered.

I have the Myth Box reading all the media from my WindowsHomeServer which also is built using this same Atom Mother Board:


Thank You so much guys!!!!!

---

### Post by MikeInParadise on 2009-04-24
I decided to go ahead and upgrade my MythBuntu 8.10 to 9.04 yesterday and take a chance with the SVideo Still working.

What happened is the SVideo is recognized but the Sync is out and the video is rolling.   This is exactly what it looked like before appling eh new /etc/X11/xorg.conf file.

I check this file and here is what the Upgrade did to the xorg.conf
```
 xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg
#MIke====2009-04-15-Use Sample From Video Patch
Section "ServerLayout"               
        Identifier     "Default Layout"
        Screen      0  "Screen0" 0 0       
# commented out by update-manager, HAL is now used
#        InputDevice    "Keyboard0" "CoreKeyboard"
EndSection                                       

Section "Files"
		 ModulePath   "/usr/lib/xorg/modules"
		 FontPath     "/usr/share/fonts/misc/"
		 FontPath     "/usr/share/fonts/TTF/"
		 FontPath     "/usr/share/fonts/OTF"
		 FontPath     "/usr/share/fonts/Type1/"
		 FontPath     "/usr/share/fonts/100dpi/"
		 FontPath     "/usr/share/fonts/75dpi/"
EndSection

Section "ServerFlags"
        Option      "AIGLX" "on"
EndSection                      

# commented out by update-manager, HAL is now used
#Section InputDevice"                                                  
#                                                                       
## keyboard added by hpxl                                              
#        Identifier  Keyboard0"                                        
#        Driver     "kbd"                                              
#        Option      "XkbModel" pc105+inet"                            
#        Option      "XkbLayout" us"                                   
#EndSection                                                             

                                                                       

Section "Device"
        Identifier  "Card0"

        #Identifier      "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        Option          "monitor-VGA"  "VGA"
        Option          "monitor-TV"   "TV"
        Option          "monitor-LVCD" "LVCD"
EndSection

Section "Monitor"
        Identifier      "VGA"
        Option "Ignore" "false"
EndSection

Section "Monitor"
        Identifier      "LVCD"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "TV"
        Option  "Ignore" "false"
EndSection

Section "Screen"
		 Identifier		 "Screen0"
		 Monitor		  "TV"
		 Device		 	 "Card0"
		 DefaultDepth 24
		 SubSection "Display"
	 		 Depth		  24
	 		 Modes		  "1024x768"
		 EndSubSection

EndSection
```

Now seeing as I just did the original driver change without really understanding what was happening I am not sure how to go about fixing this.

Seems like the xorg.conf was only changed with regards to the keyboard so that should not affect it.

Originally I had not SVideo out and now the I applied the Intel driver update in 8.10 I got this out of sync video and I am making the assumption that this is still applied as I am getting Svideo out.  

Question: Is that true and how can I verify what video driver is actually being used? 

Question: On MythBuntu I have a lot less options on the system menu available to me. Where do I find the s-video TV out configuration.

Any thoughts on fixing the Syncing

---

### Post by Ibn al-Hazardous on 2009-04-25
> **MikeInParadise said:**
> I decided to go ahead and upgrade my MythBuntu 8.10 to 9.04 yesterday and take a chance with the SVideo Still working.

What happened is the SVideo is recognized but the Sync is out and the video is rolling.   This is exactly what it looked like before appling eh new /etc/X11/xorg.conf file.
-----8<--------8<--------8<-----
Originally I had not SVideo out and now the I applied the Intel driver update in 8.10 I got this out of sync video and I am making the assumption that this is still applied as I am getting Svideo out.  

Question: Is that true and how can I verify what video driver is actually being used? 

Question: On MythBuntu I have a lot less options on the system menu available to me. Where do I find the s-video TV out configuration.

Any thoughts on fixing the Syncing

I made a clean install with Mythbuntu, and then added the driver according to the instructions here - and it worked for me. I had to make some special fix-ups, but since you had it working on 8.10 - I suppose you never needed them. Did you make a reinstall of the drivers after the upgrade though? I suppose Ubuntu 9.04 contains an upgrade to X.org, which would install the 2.6 version of the drivers - over your custom ones. Another source of rolling screens could be if you also have a VGA monitor connected. When I do that, there is no stopping the rolling TV screen.

If my suggestions don't help, you might want to check my write-up on [how I got my htpc working]("http://blueturtle.nu/ibn/blog/45/htpc-or-hmc-whatever-part-deux"). It could be that some of the other stuff I detail there may help you.

---

### Post by MikeInParadise on 2009-04-26
> **Ibn al-Hazardous said:**
> 
Did you make a reinstall of the drivers after the upgrade though? I suppose Ubuntu 9.04 contains an upgrade to X.org, which would install the 2.6 version of the drivers - over your custom ones. Another source of rolling screens could be if you also have a VGA monitor connected. When I do that, there is no stopping the rolling TV screen.


No I did not make a reinstall of the drives after doing  9.04.  Originally on 8:10 I got nothing on the SVideo. Then I applied the Intel driver and got the rolling screen on SVideo out with my VGA monitor hooked up and workng fine.   I applied the xorg.conf and that fixed the SVideo out.  This worked fine with a monitor hooked up at the same time.

I wanted to see if there was some way to check which driver was actually being using.

Anyways I have some "Honey Do" items around the house that I have to do this week (Crown Moldings, Hardwood floor) now so I am going to have to sneak in any time I want to play with this.

Thanks for the reply...

---

### Post by neffer on 2009-04-27
I had the same problems with the TV-out on the Intel D945GCLF2, but I got a very easy solution from this page:
[https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/298422](https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/298422)

Simply add the backports from [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/") repositories, and update your system.

---

### Post by MikeInParadise on 2009-04-27
> **neffer said:**
> I had the same problems with the TV-out on the Intel D945GCLF2, but I got a very easy solution from this page:
[https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/298422](https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/298422)

Simply add the backports from [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/") repositories, and update your system.

Ok, while sipping my morning coffee before I am back at the crown moldings, I got the auto reply in my Email, turn on the MythBuntu media center and did the above.  You need to follow the instructions for adding the public key and I now have video out again.

If only the rest of my chores for the day would be so easy.

Thanks for this Neffer!  Great stuff!

---

### Post by yocec on 2009-09-09
Sorry for this old reply, but I can't get it work...

My configuration : 
D945GCLF2 card plug on my old CRT TV with SVIDEO output to SCART
A fresh install of Ubuntu 9.04 minimal (command line system with xorg)


I have added repository like write in comment [#24]("http://ubuntuforums.org/showpost.php?p=7159042&postcount=24") and made upgrade, so my xserver-xorg-intel-video package version is 2:2.7.1-0ubuntu1~xup~1


I have tried xorg.conf given in this thread and many other options, but nothing to do, I can' get it work.


Sometime when I'me lucky It started but not at all boot !!!


In my Xorg.0.log I can see these errors : 

```
(WW) intel(0): No outputs definitely connected, trying again...
(II) intel(0): Output VGA disconnected
(II) intel(0): Output TV-1 disconnected
(WW) intel(0): Unable to find initial modes
(EE) intel(0): No valid modes.
(II) UnloadModule: "intel"
(II) UnloadModule: "vgahw"
(II) Unloading /usr/lib/xorg/modules//libvgahw.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```


Please help me
Thanks

---

### Post by kilmarnock on 2009-10-03
Hi!
I follow this thread since I have this board (3 Months). I play with the config file now and then, but without success.

I use the launchpad version of the intel driver (2.7.1-0ubuntu1~xup~1)

The log file still says  "SDVOB: Choosing default TV format of NTSC-M", the SVideo picture is still b/w. Even exchanged the kable.

What makes me wondering is that the thread reports the self-compile of intel driver 2.7.0  working and the 2.7.1 is not.

B/W is not acceptable for a HPC. Please, if someone could confirm the 2.7.1 version working with PAL?

Felix

---

### Post by dfdario on 2009-10-20
You should wait for [this ]("http://bugs.freedesktop.org/show_bug.cgi?id=23916")bug is solved as I am waiting for.
It seems a never ending story.
I have two of D945GCLF2. One of them has mythbuntu 9.04 working fine (master-backend+frontend) but I had to connect it to my PAL TV via a VGA-to-PAL converter since.
On the second system I installed mythbuntu 9.10 beta at first but, since  it lacks tuning up tv channels, I revert to mythbuntu 9.04 with the last kernel available ([2.6.32-rc5]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32-rc5/")).
This enable me to set s-video output to PAL_B with[FONT=Arial] the command[/FONT][FONT=Arial]:  xrandr --output TV1 --mode 720x576 --set mode PAL_B as described on [this ]("http://bugs.freedesktop.org/show_bug.cgi?id=22891")bug already fixed[/FONT].
Unfortunately until the bug #[23916]("http://bugs.freedesktop.org/show_bug.cgi?id=23916") will not be solved even if PAL_B has been set no PAL s-video out would be properly work.
We should all wait for ykzhao fix this bug.

[EMAIL="yakui.zhao@intel.com"][/EMAIL]

---

### Post by kilmarnock on 2010-01-05
Still no progress. Does anyone know a good converter from DVI to SVideo? I cannot wait anymore, not having television / video support on a HPC is senceless.

Felix

---

### Post by monkeysinacan on 2010-03-18
Has anyone gotten this to work under 9.10? I'm going batty trying to get this working.

---

### Post by kilmarnock on 2010-03-19
Check out dfdario' s link. The maintainer of the driver created a patch. The kernel is not available for ubuntu, so you have to compile one for yourself.

---

### Post by monkeysinacan on 2010-03-19
Thanks, but I should have specified. I'm trying to get it to work for NTSC. I tried neffer's method
> **neffer said:**
> I had the same problems with the TV-out on the Intel D945GCLF2, but I got a very easy solution from this page:
[https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/298422](https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/298422)

Simply add the backports from [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/") repositories, and update your system.

 and installed the backports in Jaunty but had no success in getting the s-video to work. Does anyone know what I could be doing wrong? :-k
Thanks again.

---

### Post by monkeysinacan on 2010-03-20
Well don't I feel silly. It looks like it did work. I had been testing it with a portable DVD player that also had video in on it. Then I decided to try it with an actual TV and it works perfectly now. :D

---

### Post by dfdario on 2010-03-21
Bug #[23916]("http://bugs.freedesktop.org/show_bug.cgi?id=23916") has been solved then applying the patch should solve.

---

### Post by dfdario on 2010-04-01
[FONT=&quot]As far as is stated in #[/FONT][FONT=&quot][23916]("http://bugs.freedesktop.org/show_bug.cgi?id=23916")[/FONT][FONT=&quot] Lucid won't be affected. In fact[/FONT][FONT=&quot] the patch [/FONT][FONT=&quot]will[/FONT][FONT=&quot] [/FONT][FONT=&quot]be[/FONT][FONT=&quot] [/FONT][FONT=&quot]backported[/FONT][FONT=&quot] [/FONT][FONT=&quot]to[/FONT][FONT=&quot] 2.6.32.[/FONT]

---

### Post by Someone09 on 2010-05-15
On xbmc live based on ubuntu 9.10 (I think), when plugging my ntsc TV by s-video, I get mostly black and white with weird color and some sort of flickering. I tried adding the ppa as said earlier but it did not work. Anybody able to help me or point me to the solution ?

---

