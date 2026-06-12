---
title: "Breezy performance issue with hard drive accesses and XOrg on Inspiron 9100"
date: 2006-03-28
forum: Hardware &amp; Laptops
---

### Post by doranchak on 2006-03-28
(UPDATE: I'm suspecting the wireless drivers now, since when I am on a wired network I do not encounter these CPU usage spikes during high disk activity.  See end of post.)

I am being frustrated by a performance issue with my Dell Inspiron 9100 laptop running Breezy.  The basic problem is that when there is a decent amount of hard drive activity, the CPU usage spikes and the entire system performance degrades.  The "top" command will show Xorg as the biggest offender.  I am baffled to why XOrg would be affected by the disk access.  I can understand why disk access will slow the machine down in general, but even a simple large-file write operation makes the machine completely unusable at times.

If the disk activity goes on long enough, then when I kill the process behind whatever is generating the disk activity, the performance degradation becomes "sticky" and the CPU usage remains extremely high, making the system very sluggish.  But the system will recover if I don't let the disk activity go on for too long.  It is as if there is a lot of buffer/cache activity, and when the disk access stops, the machine is still processing buffer/cache (I have no evidence to back this hunch).

At first I spent a lot of time blaming ATI for their crappy drivers.  But it seems like no matter which drivers I use, the problem persists.  Here is the version I am running (from the output of "glxinfo"):

```

OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 2.0.5695 (8.23.7)

```

I installed these drivers using [these instructions]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_newer_8.23.7_drivers_in_Breezy_Badger")

If I revert back to the Mesa generic open source drivers, the performance is still terrible because of the lack of direct rendering.

The other thing I looked into was hard disk parameters via hdparm.  I made sure DMA was enabled (it is).  I tried performing the tweaks in this HOWTO: [http://ubuntuforums.org/showthread.php?t=24416]("http://ubuntuforums.org/showthread.php?t=24416")  Alas, the problem still remains.  Here is my hdparm info for the drive in question:

```

/dev/hda:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 65535/16/63, sectors = 117210240, start = 0

```

Could anyone help point me in a direction that can help troubleshoot the problem?  One thing I need is a way to figure out what the disk drive is up to - is there some kind of monitor I can look at to see what the drive is doing whenever the system performance is degrading?

UPDATE: I strongly suspect this is due to my wireless drivers.  I think when there is a lot of network activity via my wireless interfaces, the CPU usage will spike.  When I am on a wired network (ethernet), the problem does not occur.  I am running ndiswrappers version 1.1-4ubuntu2 for the laptop's built in wifi.  I haven't been using it lately, however - lately I've been using a Netgear PCMCIA card, model MA401, which Ubuntu auto-detects for me without using ndiswrappers.  Perhaps these drivers are problematic.

Does anyone else have this problem?  The sad thing about this is I have an Inspiron 8200 running Windows XP, and it can initialize an instance of JBoss running a big java application in about half to a third of the amount of time it takes to do the same thing in Breezy.  And the Inspiron 8200 is an inferior machine to the Inspiron 9100!  BTW my filesystem in Breezy is ext3, and I'm running Gnome.  My kernel is 2.6.12-10-686-smp.

Another thing I tried that didn't seem to make any difference: adding kernel parameters to disable ionotify and power management.

Thanks in advance for any help!

---

### Post by doranchak on 2006-04-01
Well, ignore all of the above.  I am an idiot.  The real problem was that the fans were clogged up with a few years' worth of dust!

This link is what saved me from tossing the laptop out the window:
[http://ubuntuforums.org/showthread.php?p=882838#post882838]("http://ubuntuforums.org/showthread.php?p=882838#post882838")

---

