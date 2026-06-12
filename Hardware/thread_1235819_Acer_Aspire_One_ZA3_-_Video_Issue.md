---
title: "Acer Aspire One ZA3 - Video Issue"
date: 2009-08-09
forum: Hardware
---

### Post by sean.bales on 2009-08-09
I recently purchased an Acer Aspire One model ZA3.  I loaded Jaunty on it and was very happy to find that just about everything works.  The webcam works, touchpad, wireless, etc.  I didn't really have to tweak anything.  The one problem I am having is the video.  The video works and I can get 1024x768 resolution, but it will not let me run in 1366x768 which is the native resolution of this 11.6" screen.  I could live with 1024x768 but the other problem is much worse.  The video is very choppy.  Watching video is impossible.  I get one frame of video per second if I'm lucky and it doesn't matter what type of video it is.  Flash, avi, even the webcam causes this choppiness.

I have already scowered the forums for help and discovered this to be a common problem on the Acer Aspire One netbooks but they all lead to the same solution(s).  Either install the Poulsbo driver and/or enable/fix mtrr.

These are the instructions I have already followed to install the PSB driver.[INDENT]A.P. Says:
June 9, 2009 at 2:13 pm | Reply

There is basic video support for the Intel Poulsbo chip. Please execute the following steps to get native suport for 1366×768 (but no hardware acceleration!):

- add the following line at the end of /etc/apt/sources.list:
deb [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main

- execute the following commands from command line:
sudo gpg –keyserver keyserver.ubuntu.com –recv 0×99d6b21cc6598a30
sudo apt-get update
sudo apt-get install xserver-xorg-video-psb

- reboot
[/INDENT]When I follow these directions, when I reboot I don't get X at all.  It crashes telling me the hardware is unrecognized.

I also followed a guide for configuring the mtrr register but when I run the command lspci -v and look for the VGA adapter, I don't see a register that has write-access.  They all say read-only.

Anyways, I started this thread because I have not been able to find a thread specific to the ZA3 and since the solutions for the other Acer Aspire Ones is not working can someone help me?

Thank you!

Sean Bales

---

### Post by sean.bales on 2009-08-09
Some additional information..,.

sean@mini:~$ sudo lspci -v | grep -A 10 VGA
00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)
    Subsystem: Acer Incorporated [ALI] Device 0244
    Flags: bus master, fast devsel, latency 0, IRQ 7
    Memory at b0080000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 1800 [size=8]
    Memory at c0000000 (32-bit, non-prefetchable) [size=256M]
    Memory at b0000000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: [d0] Power Management version 2
    Capabilities: [b0] Vendor Specific Information <?>
    Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

sean@mini:~$ 

sean@mini:~$ sudo cat /proc/mtrr 
reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg01: base=0x07f700000 ( 2039MB), size=    1MB, count=1: uncachable
reg02: base=0x07f800000 ( 2040MB), size=    8MB, count=1: uncachable
sean@mini:~$

---

### Post by p.herewini on 2009-08-17
Hello, I just got an Aspire One ZA3 myself and experienced the same problems. After installing the latest Netbook Remix of Ubuntu everything went unbearably slow. I had to install "normal" Jaunty and had a slight improvement in performance. Although the resolution was still stuck on 1024x768, and couldn't change to 1366x768. Video was also unwatchable.

After following this fix I managed to get 1366x768 resolution working:
Enabling 1366x768 Resolution on AspireOne 751h (11.6")
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

Although I still cannot get video working and I'm pretty sure this problem is also effecting other performance such as scrolling etc.

Have you had any luck with your ZA3? I really don't want to go back to windows on my brand-new netbook!?

---

### Post by p.herewini on 2009-08-18
RESOLVED!

After trying all-sorts of bug-fixes including adding *enable_mtrr_cleanup mtrr_spare_reg_nr=1* to grub I finally stumbled onto this ridiculously simple solution:

1. If you haven't got the native 1366x768 resolution working yet, try this:
> Enabling 1366x768 Resolution on AspireOne 751h (11.6")

With this variant (popular because it's available at Costco), the maximum graphics resolution (1366x768) does not work out of the box. To install an updated graphics driver, add the following line at the end of /etc/apt/sources.list:

deb [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main

then run the following commands in the terminal:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys C6598A30

sudo apt-get update

sudo apt-get install xserver-xorg-video-psb psb-kernel-source

sudo shutdown -r now

If an update to a later version (such as an upgrade from 2.6.28-11 to 2.6.28-14) breaks the graphics driver on your 751h, continue booting to the desktop (select the Run one time session with low graphics option) then run the following commands in the terminal:

sudo apt-get remove psb-kernel-source

sudo apt-get install psb-kernel-source

sudo shutdown -r now

DO NOT use the --reinstall flag to attempt this fix (it will likely crash your session). Use the remove option first, followed by the install option as shown above. 

2. FIXED FULLSCREEN VIDEO PLAYBACK FOR ME:
Applications > Synaptic > Install the following
psb-kernel-headers
psb-firmware
poulsbo-driver-3d
poulsbo-driver-2d
xpsb-glx
psb-modules

I'm not experienced enough to know exactly what each of these packages do, but after installing these and restarting, fullscreen video FINALLY started working smoothly.

---

### Post by sean.bales on 2009-08-23
So I followed your directions and it worked!  The screen resolution is now what it should be and the video playback is no longer choppy...
 
...BUT...
 
Now the whole system is unstable under Ubuntu.  If I leave it running for more than about 15 minutes, it freezes solid.  It becomes completely unresponsive to any input device.  The only way to get it back is to hard-power-reset it.
 
I have completely disabled power management thinking that maybe the new driver wasn't liking a call from acpi or something.  It didn't fix it.  If I uninstall the Poulsbo driver the system is stable again but the video problems are back.
 
Does anyone have any thoughts?

---

### Post by Polymap on 2009-08-24
Hi Sean,

I tried this and now my Acer Aspire One ZA3 runs wihout a crash more than 4 hours.

Uninstall poulsbo-driver-3d (only this one)

Edit the the file
/etc/X11/xorg.conf  
 
 
Section "Device" 
        Identifier      "Configured Video Device" 
        Option "AccelMethod" "EXA" 
        Option "DRI" "off" 
        Option "MigrationHeuristic" "greedy" 
EndSection

I hope this helps you

Thomas

---

### Post by p.herewini on 2009-08-25
One thing I have noticed that a few things aren't quite right but I'm sure this machine isn't working to its full potential. Scrolling/dragging windows and flash movies in firefox are still laggy.

So I'll take Polymap's advice and remove poulsbo-driver-3d and change my xorg device section from:
```

Identifier	"Configured Video Device"
Option		"UseFBDev"		"true"
Option          "IgnoreACPI"
Option          "AccelMethod" 		"exa"
Option          "MigrationHeuristic" 	"greedy"
Option          "NoDDC"
```

To: 
```

Identifier "Configured Video Device"
Option "AccelMethod" "EXA"
Option "DRI" "off"
Option "MigrationHeuristic" "greedy" 
```

---

### Post by p.herewini on 2009-08-25
Ok so I didn't notice much difference except the login/password font size is bigger (weird because res didn't change?) and flash video is a little smoother but still unwatchable.

---

### Post by p.herewini on 2009-08-25
> **p.herewini said:**
> Ok so I didn't notice much difference except the login/password font size is bigger (weird because res didn't change?) and flash video is a little smoother but still unwatchable.

Ok so it turns out it wasn't all flash video that is jumpy, [www.theberrics.com]("http://www.theberrics.com") is bad but youtube.com plays ok when not in fullscreen. Scrolling and dragging of windows is still pretty bad.

---

### Post by Amae on 2009-11-25
Hi,

Di you finally solve this? I have an Acer Aspire One, ZA3 also, and, it comes with Windows Vista which is terribly and unbeareably slow. Since I have linux inmy desktop computer I was exited about installing it on my laptop, I donwloaded the latest Kubuntu Netbook version to it, and everything seems to work just fine(its so fast :O) ... but the screen resolution is wrong (its got 1024.768), and except for a few "weird colors" that appear for about half a second on the startup I haven't encountered any other video problem (but I haven't tried to playvideos in it yet though). I would like to solve this problem but there are various things here and I don't know which one to try.

---

### Post by sean.bales on 2009-11-25
Just to follow up ...
 
This thread did completely resolve my video issues with Ubuntu 9.04 and I would like to express gratitude to those who helped me.  Thank you!  I am still running 9.04 and I'm pretty happy with it.  I wish I could upgrade to 9.10.
 
I have recently attempted to upgrade to Ubuntu 9.10 on the same Acer Aspire One ZA3 and that has been met with sure failure.  I tried to do a dist-upgrade and that pretty much made the OS unable to boot, even if I tried a previous kernel from the Grub menu.  I can not even get a live distro (built from USB) of 9.10 to boot.  I get errors about modules being unable to load.  I have tried both usb-creator.exe for Windows, usb-creator from a good 9.10 install on a different box, and unetbootin 377.
 
Has anyone else tried?  Any successes?
 
Thanks,
Sean

---

### Post by phantom21 on 2009-12-03
Purchased the Acer Aspire One ZA3 a few days ago (Black Friday, Radio Shack) and installed Kubuntu Karmic (9.10) and have to say I'm very happy with it.  It gets everything, WiFi, wired, webcam, USB, etc.

My video is also at 1024X768 and I'd like to know if the instructions above will work with that before trying it.

Also, has anyone bought a larger battery for it, one of the 6 cells or even the 9 cell ones?  All the ones I'm seeing are for the ZG5 and have a different number than I'm expecting.

Thanks,

Mark

---

### Post by macachis on 2009-12-06
To phantom21:

There's other topic in this forum about this same problem ([http://ubuntuforums.org/showthread.php?t=1204386&page=2](http://ubuntuforums.org/showthread.php?t=1204386&page=2)). There, I found this solution and, for me, works fine:

[FONT=Arial]sudo apt-get update
sudo apt-get upgrade
[restart]
sudo wget [http://gma500re.altervista.org/scripts/poulsbo_ppa.sh](http://gma500re.altervista.org/scripts/poulsbo_ppa.sh) && sh ./poulsbo_ppa.sh
[restart]

About the battery. I bought my za3 with a six cell battery and for me it's perfect. I can run my netbook for 7 hours. But I don't know if its possible to buy the battery alone.

To [/FONT]sean.bales:

I have updated from UNR 9.04 to UNR 9.10. In fact, I made a clean install of 9.10 from a USB, overwritting the previous version. I have a dual-boot with WindowsVista so, first of all, I recovered the mbr from Win. Then, I plugged the pendrive with UNR and made the installation. I only formatted the partition with Ubuntu in it. And I have no problems! (Ok, afterwards I have to fix de video issue and change some things to have it as I like, but everything works fine)

Hope this helps you!

---

### Post by KingLear0 on 2009-12-07
Hey all --

I (like a moron) went ahead an updated my kernel yesterday from the *.31-14 to *.31-16 (the most recent in the Update Manager).  

On the -14 Kernel I had everything working just fine by using the poulsbo_ppa.sh script.  As always, updating the kernel broke my Aspire One.  From my previous reading, I thought that what I needed to do was boot up, connect online, and run:

sudo apt-get remove psb-kernel-source
sudo apt-get install psb-kernel-source

So I went an ran that, and the psb-kernel-source has an error when it tried to reinstall.  So, I tried just running the entire poulsbo_ppa.sh script again, same error (it wouldn't complete the install, sorry I don't have the exact error text handy, I will try to post it later today)


So, my main questions are:

1)  Has anyone successfully updated to the most recent kernel and kept the video working?
2)  Is there a new version of the psb-kernel-source that I was unable to find that will work with the *-16 kernel?
3)  Am I missing something really, really obvious and that's why I haven't seen any other mention of this error regarding kernel upgrades?

Thanks in advance!

---

### Post by deobotha on 2010-01-15
> **Amae said:**
> Hi,

Di you finally solve this? I have an Acer Aspire One, ZA3 also, and, it comes with Windows Vista which is terribly and unbeareably slow. Since I have linux inmy desktop computer I was exited about installing it on my laptop, I donwloaded the latest Kubuntu Netbook version to it, and everything seems to work just fine(its so fast :O) ... but the screen resolution is wrong (its got 1024.768), and except for a few "weird colors" that appear for about half a second on the startup I haven't encountered any other video problem (but I haven't tried to playvideos in it yet though). I would like to solve this problem but there are various things here and I don't know which one to try.

Hi, I followed these steps with sucess!! Even Compufiz works - Although its laggy. 
[COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**wget**[/COLOR] http:[COLOR=#000000]**//**[/COLOR]gma500re.altervista.org[COLOR=#000000]**/**[/COLOR]scripts[COLOR=#000000]**/**[/COLOR]poulsbo.sh [COLOR=#000000]**&&**[/COLOR] [COLOR=#C20CB9]**sh**[/COLOR] .[COLOR=#000000]**/**[/COLOR]poulsbo.sh
[COLOR=#C20CB9]**sudo**[/COLOR] gedit [COLOR=#000000]**/**[/COLOR]etc[COLOR=#000000]**/**[/COLOR]X11[COLOR=#000000]**/**[/COLOR]xorg.conf

Replace everything with the following:
Section [COLOR=#993333]"Device"[/COLOR]
	Identifier	[COLOR=#993333]"GMA500"[/COLOR]
	Option		[COLOR=#993333]"AccelMethod"[/COLOR] [COLOR=#993333]"EXA"[/COLOR]
	Option		[COLOR=#993333]"DRI"[/COLOR] [COLOR=#993333]"on"[/COLOR]
	Option		[COLOR=#993333]"MigrationHeuristic"[/COLOR] [COLOR=#993333]"greedy"[/COLOR]
	Option		[COLOR=#993333]"IgnoreACPI"[/COLOR] [COLOR=#993333]"yes"[/COLOR]
	Driver	 	[COLOR=#993333]"psb"[/COLOR]
EndSection
 
Section [COLOR=#993333]"DRI"[/COLOR]
    Mode    0666
EndSection

[COLOR=#C20CB9]**sudo**[/COLOR] gedit [COLOR=#000000]**/**[/COLOR]usr[COLOR=#000000]**/**[/COLOR]bin[COLOR=#000000]**/**[/COLOR]compiz
Change this: 
# Driver whitelist
[COLOR=#000099]WHITELIST[/COLOR][COLOR=#000066]**=**[/COLOR][COLOR=#993333]"nvidia intel ati radeon radeonhd i810 fglrx"

To This:
[/COLOR]# Driver whitelist
[COLOR=#000099]WHITELIST[/COLOR][COLOR=#000066]**=**[/COLOR][COLOR=#993333]"nvidia intel ati radeon radeonhd i810 fglrx psb"

Hope it works !! Let me know via email
[/COLOR]

---

### Post by ciclopropano on 2010-05-26
from my computer (lucid-lynx) Im not being able to even download the psb-kernel-source
when I try to follow the instructions given by p.herewini
I guess the source is outdated or something :S can somebody post an updated url to download the driver from PLEASE!!!

---

### Post by ciclopropano on 2010-05-26
> **p.herewini said:**
> RESOLVED!

After trying all-sorts of bug-fixes including adding *enable_mtrr_cleanup mtrr_spare_reg_nr=1* to grub I finally stumbled onto this ridiculously simple solution:

1. If you haven't got the native 1366x768 resolution working yet, try this:


2. FIXED FULLSCREEN VIDEO PLAYBACK FOR ME:
Applications > Synaptic > Install the following
psb-kernel-headers
psb-firmware
poulsbo-driver-3d
poulsbo-driver-2d
xpsb-glx
psb-modules

I'm not experienced enough to know exactly what each of these packages do, but after installing these and restarting, fullscreen video FINALLY started working smoothly.

it tells me I need libdrm-poulsbo1
but when I try to install that it tells me it has to erease a lot of files from my computer - what should I do??:(

---

### Post by p.herewini on 2010-06-04
I was also experience the same problem after my housemates updated my system and I had to choose the older kernel from grub. Now thanks to deobotha, all I do is install any updates, restart into the new kernel (which starts in the wrong resolution of 1024x768 ) and run deobotha's fix:

> **deobotha said:**
> [COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**wget**[/COLOR] http:[COLOR=#000000]**//**[/COLOR]gma500re.altervista.org[COLOR=#000000]**/**[/COLOR]scripts[COLOR=#000000]**/**[/COLOR]poulsbo.sh [COLOR=#000000]**&&**[/COLOR] [COLOR=#C20CB9]**sh**[/COLOR] .[COLOR=#000000]**/**[/COLOR]poulsbo.sh
[COLOR=#C20CB9]**sudo**[/COLOR] gedit [COLOR=#000000]**/**[/COLOR]etc[COLOR=#000000]**/**[/COLOR]X11[COLOR=#000000]**/**[/COLOR]xorg.conf

Replace everything with the following:
Section [COLOR=#993333]"Device"[/COLOR]
	Identifier	[COLOR=#993333]"GMA500"[/COLOR]
	Option		[COLOR=#993333]"AccelMethod"[/COLOR] [COLOR=#993333]"EXA"[/COLOR]
	Option		[COLOR=#993333]"DRI"[/COLOR] [COLOR=#993333]"on"[/COLOR]
	Option		[COLOR=#993333]"MigrationHeuristic"[/COLOR] [COLOR=#993333]"greedy"[/COLOR]
	Option		[COLOR=#993333]"IgnoreACPI"[/COLOR] [COLOR=#993333]"yes"[/COLOR]
	Driver	 	[COLOR=#993333]"psb"[/COLOR]
EndSection
 
Section [COLOR=#993333]"DRI"[/COLOR]
    Mode    0666
EndSection

[COLOR=#C20CB9]**sudo**[/COLOR] gedit [COLOR=#000000]**/**[/COLOR]usr[COLOR=#000000]**/**[/COLOR]bin[COLOR=#000000]**/**[/COLOR]compiz
Change this: 
# Driver whitelist
[COLOR=#000099]WHITELIST[/COLOR][COLOR=#000066]**=**[/COLOR][COLOR=#993333]"nvidia intel ati radeon radeonhd i810 fglrx"

To This:
[/COLOR]# Driver whitelist
[COLOR=#000099]WHITELIST[/COLOR][COLOR=#000066]**=**[/COLOR][COLOR=#993333]"nvidia intel ati radeon radeonhd i810 fglrx psb"
[/COLOR]

sean.bales, you should update your first post with this info for new visitors as I believe this is the best fix.

---

### Post by p.herewini on 2010-06-04
Ok so it seems now my acer aspire one will not wake from sleeping anymore. The power comes back on but the screen and keyboard do not come back. Is anyone else having this problem, who also used deobotha's solution?

---

