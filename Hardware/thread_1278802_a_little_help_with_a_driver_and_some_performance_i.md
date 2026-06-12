---
title: "a little help with a driver and some performance issues"
date: 2009-09-30
forum: Hardware
---

### Post by X1R1 on 2009-09-30
Hello all, I recently installed jaunty on my Acer Aspire 5810TZ laptop and im pretty happy with the results, at first ubuntu wont recognize the cd drive but after upgrading it worked great. The only current thing not working is the webcam that comes with the laptop, called Crystal Eye.

Now I know this has been asked before and I checked some post before posting this, but the other posts werent helpful. 


The other issue im having is regarding performance, sometimes when I alt+tab to another application or things like that, ubuntu changes between windows very slow and sometimes locks up. Also firefox has problem with youtube videos in fullscreen mode, they play very slow but audio is fine. Maybe that has something to do with my card drivers or something, here is the output of lspci:

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 Ethernet controller: Attansic Technology Corp. Device 1063 (rev c0)
02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

Im pretty happy with ubuntu but I would like to resolve those issues, also the webcam thing will get lots of attention.

---

### Post by DJonsson2008 on 2009-09-30
What CPU are you using?

How much RAM do you have?

What video driver are you using?

Are there any other apps running
when you run your videos?

Have you tried loading Xubuntu desktop to free some
resources. You can run this with Ubuntu and select
at the boot prompt, loading a lighter desktop, 
can free some resources, not sure if its a 100%
solution in this case but I've found it snappier.

---

### Post by X1R1 on 2009-09-30
> **DJonsson2008 said:**
> What CPU are you using?

How much RAM do you have?

What video driver are you using?

Are there any other apps running
when you run your videos?

Have you tried loading Xubuntu desktop to free some
resources. You can run this with Ubuntu and select
at the boot prompt, loading a lighter desktop, 
can free some resources, not sure if its a 100%
solution in this case but I've found it snappier.

CPU: Genuine Intel(R) CPU U2700  @ 1.30GHz
RAM: 3Gb and upgrading to 6 within the next week.
VIDEO: Mobile 4 Series Chipset Integrated Graphics Controller

video is integrated in motherboard, dont know where to find which driver uses.

No other apps running when I test it, only the wireless, volume control and battery ones. And no I havent tried the xubuntu thing, cause I think the laptop its pretty good to handle a good configuration.

---

### Post by DJonsson2008 on 2009-09-30
lspci -v 

From the command line will give you information
about your video card.

I also suggest you might repost your thread as 
something like Acer Aspire 5810TZ driver issues,
this may attract other folks using the same machine,
or having experience with the same machine.

You can also search the net for your video card,
which I think is a flavor of Intel embedded card,
even though its on the motherboard it has a name
and can be identified in the machines specs.

Another process of elimination may be trying the
machine directly plugged into a lan via wire to
help see if a wireless issue isnt' at the heart
of it. 

Just some suggestions.

---

### Post by X1R1 on 2009-09-30
> **DJonsson2008 said:**
> lspci -v 

From the command line will give you information
about your video card.

I also suggest you might repost your thread as 
something like Acer Aspire 5810TZ driver issues,
this may attract other folks using the same machine,
or having experience with the same machine.

You can also search the net for your video card,
which I think is a flavor of Intel embedded card,
even though its on the motherboard it has a name
and can be identified in the machines specs.

Another process of elimination may be trying the
machine directly plugged into a lan via wire to
help see if a wireless issue isnt' at the heart
of it. 

Just some suggestions.

Here is the output of the lspci -v command, I just pasted here the video part:

> 00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Subsystem: Acer Incorporated [ALI] Device 022b
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	**Kernel driver in use: agpgart-intel**
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Acer Incorporated [ALI] Device 022b
	Flags: bus master, fast devsel, latency 0, IRQ 2300
	Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 4110 [size=8]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [d0] Power Management version 3

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Acer Incorporated [ALI] Device 022b
	Flags: fast devsel
	Memory at d4500000 (64-bit, non-prefetchable) [disabled] [size=1M]
	Capabilities: [d0] Power Management version 3

And yeah, I have tried the machine with wired internet access, no problems with that or the wireless card (both work perfectly). I was just stating in the previous post the apps I always have running.

The line in highlighted in bold text I think is the driver in use, can anyone confirm is there is a better driver for this card?

thanks for the help, and good idea djonsson, im changing the thread name.

regards

---

### Post by dwinks on 2009-09-30
Upgrade to Karmic and all of the issues you listed here will go away.  I have the same laptop, the youtube, alt-tab, etc, are all because the Intel driver for Jaunty is slow and buggy.  The new one in Karmic is MUCH faster.

---

### Post by X1R1 on 2009-09-30
can you put the driver name here so I can download it, karmic is still in alpha state and I use this laptop a lot. Please do > lspci -v and put the output of the video card here please so I can see the driver name and change it accordingly.

thanks in advance!

No need to upgrade to karmic just to solve this issue, here is the solution:

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

I used the "safe" one, worked like a charm.

The webcam its still an issue.

UPDATE:
Just Solved the webcam issue. thing is you need updated drivers, to be more specific, you need V4L-DVB Device Drivers and load them into your kernel. see here:

[http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

I choosed the mercurial solution cause I find it easier and it worked for me like a charm, now all performance problems are gone and the webcam works too! I tried a video chat session with emesene and it worked, also it works with ekiga, and everything that uses Linux-UVC. you can check some of them here (skype is included!!!).

Its seems to me that this is a big accomplishment cause embedded laptop webcams are hard to get to work, and its also cool to know that there isnt any quality loss or lag in the video!

hope that helps, playing to do a how to on this so you dont have to search in different threads and websites to get this to work.

regards

---

