---
title: "Dell inspiron 2600 graphics problem"
date: 2008-12-14
forum: Hardware
---

### Post by KonradKathan on 2008-12-14
Hello all,

Have recently installed Xubuntu 8.10 on my Inspiron 2600
1.2ghz Celeron, 360MB ram, 20 gig HDD, Intel i830 graphics driver.

It boots up fine, but when it gets to the GUI it only shows a black screen. However when I plug in an external monitor it works just fine. i have read about problems with the i830 driver for older versions of Ubuntu and flavors thereof, but the solutions don't seem to be working for this version. i think it has something to do with the x-org file, but am unsure, and don't want to have to reinstall it again. Any ideas?

Thanks,

Konrad

---

### Post by theUg on 2009-02-05
That&#8217;s interesting. I&#8217;ve tried to install all kinds of flavours of Linux on the same laptop and always fail to get X.org working right. I don&#8217;t think I&#8217;ve ever tried to hook up external monitor to it, so I can&#8217;t speak for older Ubuntu versions, SUSE or Fedora, but I have CDs with recent Ubuntu versions, and Xubuntu 8.10 is the only system that works out of the box even if only with external monitor.

Regular Ubuntu 8.10, loads up, but gets to the point when it&#8217;s time to load X.org and hangs (shows black screen with mouse cursor moving, but nothing else). I had the same issue with another Intel on-board chipset on my g/f desktop which is solved by removing compiz (visual bling) as per [this topic](http://www.linuxquestions.org/questions/ubuntu-63/virgin-8.10-install-hangs-after-login-692742/). So I&#8217;m sure, I&#8217;d get it to work on external monitor as well, after installing it and following instructions from that thread.

I couldn&#8217;t find 8.04 CD, but I&#8217;m curious if it would work with external monitor, cause it worked fine with aforementioned g/f desktop until upgrade to 8.10 and new Intel driver that has issues with compiz.

* * *

Anyway, the issue, it seems, is with X.org configuration. I checked the log files and found no errors. It showed that both VGA and LVDS (internal screen) are connected (I ran the machine setting monitor &#8220;Simul-Mode&#8221; in BIOS). But xorg.conf only has generic settings (&#8220;Default Screen&#8221; *etc.*) and no specifics regarding the internal screen nor the fact that computer has two monitors connected. If we could figure out proper config for the screen and monitor, I am confident it would work now.

---

### Post by mightyQ on 2009-02-08
There is a writeup here:
[http://linugadgetech.blogspot.com/2008/09/ubuntu-video-configuration-on-dell.html](http://linugadgetech.blogspot.com/2008/09/ubuntu-video-configuration-on-dell.html)

about editing xorg.conf to set it up for Inspiron 2600.

I am trying at this moment to get it going, but I am a linux newbie and cannot even find xorg.conf. 
Any idea where it shold be on a new ubuntu 8.10 installation?

Find xorg.conf shows no result, so I am puzzled.

I too installed it in safe graphics mode, and have black screen when it actually loads from the HD and runs.

I can get into the recovery mode ok from the grub bootup, but can't find the config file.  

Any assistance would be most welcome.

---

### Post by mightyQ on 2009-02-08
Never mind.
I have been away from linux a LONG time and forgot it was case sensitive.
It's going to be a long evening.

---

### Post by theUg on 2009-02-18
I actually had solved the problem about a week ago, just didn&#8217;t have time to post. I&#8217;d posted [a write-up](http://theug.pp.ru/en/information-technology/linux/finally-linux-worked-on-dell-inspiron-2600/) on that, but the long story short here&#8217;s xorg.conf that works on the fresh Xubuntu 8.10 install on Inspiron 2600 without degrading the BIOS:
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"intel"
	Option		"monitor-LVDS" "Configured Monitor"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Option		"PreferredMode" "1024x768"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

---

### Post by teratomata on 2009-03-04
None of this worked for me, nor anything else from googling Dell Inspiron 2600 xubuntu (or ubuntu or linux, etc)

Finally, I found this configuration works perfectly!

Section "Device"
	Identifier	"Intel i830"
	Driver		"i810"
	VideoRam	32768
#	Option		"UseFBDev"		"true"
EndSection

Section "Device"
	Identifier	"Linux Frame Buffer"
	Driver		"fbdev"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	HorizSync	28-49
	VertRefresh	43-72
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel i830"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
EndSection


From about half way through this [http://www.geocities.com/kymacpherson/linux/debian_i2600.html](http://www.geocities.com/kymacpherson/linux/debian_i2600.html)

To do it, just load in recovery mode, tell it to reset your x config (last option), and then run command line and nano /etc/X11/xorg.conf to have the above lines.

This is on xubuntu 8,04, with bios A08.

---

### Post by ballpointpenguin on 2009-03-04
It also works on xubuntu 8.10!

In my case, I was also battling with having a USB RT73-based wireless dongle. I had installed the SerialMonkey drivers by hand, and then found out that 8.10 supported the RT73 out of the box. Then, once I started the installation, I found that it didn't like the i830 graphics board anymore - kept identifying it as i810.

I offer my thanks to the gentle soul who showed me how to get my system back up and running, and so saved it from a fate worse than being relegated under the washing machine to balance the load... (right next to my copy of *Das Kapital*... :) )

---

### Post by theUg on 2009-03-04
> **teratomata said:**
> None of this worked for me&#8230;

&#8230;with bios A08.
I don&#8217;t know if that&#8217;s the culprit, but my solution worked with the latest BIOS, A11. And, as far as I know, newer "intel" driver is preferred to older "i810".

Your solution and others like that I&#8217;ve tried look over the top complicated. My configuration was also somewhat bloated until I started mixing and matching lines leaving eventually only the necessary directives.

P. S. As far as I could see, my config works with 24bit colour by default, by the way.

---

### Post by KonradKathan on 2009-03-15
Thank you TheUG!

I applied your solution and it booted into the GUI!!!
although the route i took was a little circuitous.

I installed Ubuntu 8.04 first, but that kept hanging, couldn't find a fix for that, so i upgraded to 8.10, and then started looking around for solutions again. Yours was the only one that has worked for me!!

In the meantime i used puppy Linux which was the only one i could get to run on my machine. went back to Ubuntu, far more comfortable!

Thanks again!

Konrad

---

### Post by pbachmann on 2009-04-11
Hello Guys.  I am new to the Linux Experince and have installed the Ubuntu 8.10 on my old DELL Inspiron 2600.

I did install with safe graphics mode and that worked.

I have tried to have better Resolution that 600x400 by tweaking the xorg.conf as indicated in the various posts here and nothing works.  I get a pastel orange screen in good resolution with the mouse arrow and everything stops there. Nothing else loads.

Any help is really appreciated.  Cheers. P

---

### Post by theUg on 2009-04-12
> **pbachmann said:**
> I get a pastel orange screen in good resolution with the mouse arrow and everything stops there. Nothing else loads.
That&#8217;s a different issue with new intel drivers not being able to work with Compiz (interface graphical effects). I already posted the link earlier here: [http://www.linuxquestions.org/questions/ubuntu-63/virgin-8.10-install-hangs-after-login-692742/](http://www.linuxquestions.org/questions/ubuntu-63/virgin-8.10-install-hangs-after-login-692742/).

---

### Post by kessaris on 2009-05-04
Any news about 9.04?

Following these instructions doesn't seem to work.. the graphics card initializes and then the screen goes white and looks like it's burning!

By the way, this is with BIOS A08 on an inspiron 2600!

I have a feeling the X infrastructure has been changed in this version of ubuntu because the xorg.conf is totally empty now.. and th e changes seem to have no effect.

---

### Post by theUg on 2009-05-04
I don&#8217;t even know, cause after upgrade the system wouldn&#8217;t even boot at all on mine (with BIOS A11). It just shows that first line of &#8220;Starting up&#8221; and nothing happens after that.

As for xorg.conf not working, I&#8217;m not sure. I had modified it on my desktop and it did affect things, but I would read up on that.

---

### Post by kessaris on 2009-05-04
OK, a new development in this drama!

Apparently other people are having this problem with other laptops so there is a thread here that references a new driver:

[http://www.linuxquestions.org/questions/linux-general-1/intel-4500mhd-white-screen-problems-on-ubuntu-8.10-685578/](http://www.linuxquestions.org/questions/linux-general-1/intel-4500mhd-white-screen-problems-on-ubuntu-8.10-685578/)

Available here: [http://launchpadlibrarian.net/19868825/intel%20driver%20fix.tar.gz](http://launchpadlibrarian.net/19868825/intel%20driver%20fix.tar.gz)

and mirrored here:

[http://rapidshare.com/files/229027997/intel_driver_fix.tar.gz](http://rapidshare.com/files/229027997/intel_driver_fix.tar.gz)

containing 3 .deb files that you must install (updated intel drivers)

0.  Boot in recovery mode.
1.  download the archive and extract it.
2.  Install the 3 contained .debs with gdebi
3.  change the driver to 'intel' in your xorg.conf
4.  reboot

now, it should at least run X without giving you a flaming white screen.  Unfortunately for me however it seems that Xubuntu takes forever to load as log-in still hasn't stopped grinding away since I started writing this message!

!

---

### Post by kessaris on 2009-05-05
OK, this works for 9.04, though I'm not sure if all the steps are necessary!!

1. Install 9.04 from the alternate disk and boot into recovery mode (esc at the grub prompt)

2. Roll back the drivers as described here: [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

3. Install the drivers from here:  [http://launchpadlibrarian.net/19868825/intel%20driver%20fix.tar.gz](http://launchpadlibrarian.net/19868825/intel%20driver%20fix.tar.gz) as described above!

4. Make sure  you change the xorg.conf as per the original instructions by teratomata

booya!! works for xubuntu.. but the damned thing still takes a million years to boot for whatever strange reason.

---

