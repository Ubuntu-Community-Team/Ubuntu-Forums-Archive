---
title: "HP dm4t / ATI Mobility Radeon HD 6370 / Switchable Graphics"
date: 2011-01-31
forum: Hardware
---

### Post by cully on 2011-01-31
I have a new HP dm4t laptop with an ATI Mobility Radeon HD 6370 graphics card.  I installed Ubuntu 10.10 64-bit (Maverick Meerkat) on it and everything seems to be working just fine.  However, in the past I've had the problem of things seeming to work fine, but certain hardware components not being enabled (e.g. the second core of my CPU).  So, there are a couple things I want to make sure of:

(1) This laptop has two VGA controllers.  One Intel integrated one, and the ATI one (the graphics card).  How do I find out if Ubuntu is using the ATI one?

(2) How do I find out if I have the best/latest driver for this graphics card?

(3) Is it best to use the proprietary driver, or the community one?  How do I find out which one I'm currently using?

These are the appropriate lines from lspci:

```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Device 68e4
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
```

Thanks!

---

### Post by Dial Tone on 2011-02-17
I have the same laptop w/10.10 x64 installed. As far as I can tell, both cards are powered on at once. When I'm on battery, I barely get 90mins of uptime.

When I tried to use the fglrx driver that was prompted by the update manager, I got the boot-to-black screen result and had to remove it.

I'm trying to at least disable the ATI card so I can get some more battery life but I can't seem to get it to disable completely.

I have tried the following:

Mine shows it works as well, but the card is still enabled because the battery and power rate stay the same.
[http://linux-hybrid-graphics.blogspot.com/2010_08_01_archive.html](http://linux-hybrid-graphics.blogspot.com/2010_08_01_archive.html)

I made a script like this but for ATI with this line: echo '\_SB.PCI0.P0P2.PEGP._OFF' > /proc/acpi/call but still no go.
[http://robbyx.net/blog/?p=190](http://robbyx.net/blog/?p=190)

This guy makes it sound so easy but whatever reason, it doesn't seem to work on my dm4: [http://ubuntuforums.org/showthread.php?p=9641991](http://ubuntuforums.org/showthread.php?p=9641991)

Any help would be much appreciated. I'm very new to Linux so some of these procedures are very cryptic.

---

