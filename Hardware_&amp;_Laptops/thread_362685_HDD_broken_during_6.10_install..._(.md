---
title: "HDD broken during 6.10 install... :("
date: 2007-02-15
forum: Hardware &amp; Laptops
---

### Post by eyko on 2007-02-15
Hi there, I'm new here (not new to linux though...)

So... I was installing the latest and greatest 6.10 ISO I downloaded today and this is more or less the pseudo-log of what happened:

- I insert CD into drive
- I configure boot (language, keyboard, resolution)
- I hit the damn return key and wait for ubuntu to load completely into the desktop, a couple minutes aye.
- I launch firefox to entertain myself while the installation runs...
- I click on install icon on the desktop
- I configure everything: name, localization, etc... **even** gparted shows my /dev/hda partitions correctly, with the 40gb unused space. I also configure that: /dev/hda1 was already an ntfs partition, so i created /dev/hda2 for swap and /dev/hda3 for /
- Next, next, next... configures partitions, creates new ones, and the progress bar begins to show % completed, so I continue surfing, mostly digg, some local newspaper site, and ubuntuforums to see where we at (I've been about half year away from linux, using OS X & Windows XP).
- **Then my problem(s) begin(s):** Grub asks me where it should be installed, says (hd0) as default... actually wanted to do (hd0,2), but I was lazy to set it up as boot partition so I thought, whatever, (hd0) is no problem; I hit enter, watch as **it tries to install grub but returns a fatal error: grub couldn't install on hd0**. I think to myself... **WTF**?

Okay, at this moment I think to myself... no problem, I can do it manually... so I launch gnome-terminal, go into /target and check /target/boot/grub... Not configured!? Hell I'm not gonna do this tonight (it was about 2:00 a.m), I'll do tomorrow... Reboot...

NTLDR not found (or whatever). Hm.. now I was worried... returned to the ubuntu CD, tried to install...this time I would use the console cfdisk manually...

ubuntu@ubuntu:~$ sudo cfdisk /dev/hda
FATAL ERROR: CANNOT READ /dev/hda (well maybe not exactly those words, but you get where I'm going...)

So, now my HDD is useless, all my partitions gone (gparted actually showed the hard disk without partitions) and I'm about to jump from my balcony and put an end to my suffering (not really). I had all my university work there with no backups :__(

Anyway... I guess life goes on, but I ain't got a buck so I can't really buy a new HDD now, hey I'm really ****** aye, but I guess I'll get over it. Anyway, has anyone got any suggestions on how to make my HDD resurrect? If Jesus could surely my magnetic storage can... or you guys think it's dead for good?

**[SOLVED] Edit:**

[COLOR="SeaGreen"]OK, it seems at some point in the installation, the partition table got fücked up. When grub tried to install, it couldn't access the HDD anymore, so it gave the error. I tried luck with a partition recovery tool (without much faith in them, I must confess...) and went for **TestDisk**: it's GPL and it's available for Linux, Windows, Mac... etc. 

I hooked the HDD into my USB HDD case and plugged it into my Macbook, ran TestDisk and it actually recovered the partitions with no trouble... I was surprised. It asked me to reboot but it wasn't necessary, I simply switched off / on the USB drive and it loaded all the partitions... including the ubuntu install (which was completed btw -that is, except grub...-)[/COLOR]

---

### Post by dcstar on 2007-02-15
> **eyko said:**
> Hi there, I'm new here (not new to linux though...)

So... I was installing the latest and greatest 6.10 ISO I downloaded today and this is more or less the pseudo-log of what happened:

- I insert CD into drive
- I configure boot (language, keyboard, resolution)
- I hit the damn return key and wait for ubuntu to load completely into the desktop, a couple minutes aye.
- I launch firefox to entertain myself while the installation runs...
- I click on install icon on the desktop
- I configure everything: name, localization, etc... **even** gparted shows my /dev/hda partitions correctly, with the 40gb unused space. I also configure that: /dev/hda1 was already an ntfs partition, so i created /dev/hda2 for swap and /dev/hda3 for /
- Next, next, next... configures partitions, creates new ones, and the progress bar begins to show % completed, so I continue surfing, mostly digg, some local newspaper site, and ubuntuforums to see where we at (I've been about half year away from linux, using OS X & Windows XP).
- **Then my problem(s) begin(s):** Grub asks me where it should be installed, says (hd0) as default... actually wanted to do (hd0,2), but I was lazy to set it up as boot partition so I thought, whatever, (hd0) is no problem; I hit enter, watch as **it tries to install grub but returns a fatal error: grub couldn't install on hd0**. I think to myself... **WTF**?

Okay, at this moment I think to myself... no problem, I can do it manually... so I launch gnome-terminal, go into /target and check /target/boot/grub... Not configured!? Hell I'm not gonna do this tonight (it was about 2:00 a.m), I'll do tomorrow... Reboot...

NTLDR not found (or whatever). Hm.. now I was worried... returned to the ubuntu CD, tried to install...this time I would use the console cfdisk manually...

ubuntu@ubuntu:~$ sudo cfdisk /dev/hda
FATAL ERROR: CANNOT READ /dev/hda (well maybe not exactly those words, but you get where I'm going...)

So, now my HDD is useless, all my partitions gone (gparted actually showed the hard disk without partitions) and I'm about to jump from my balcony and put an end to my suffering (not really). I had all my university work there with no backups :__(

Anyway... I guess life goes on, but I ain't got a buck so I can't really buy a new HDD now, hey I'm really ****** aye, but I guess I'll get over it. Anyway, has anyone got any suggestions on how to make my HDD resurrect? If Jesus could surely my magnetic storage can... or you guys think it's dead for good?

Power it off (with the power cable out, not just the switch), wait 30 seconds and then power it back on.

If the disk doesn't respond then check all of your connectors etc. (with the power off), if it is still dead then you do have major problems.

---

### Post by eyko on 2007-02-16
I tried that, no go... but all good now, I updated the post. Thanks still :)

---

### Post by AKM on 2007-02-16
I had a somewhat similar incident. I'd just finished installing 6.1, was just starting to play around with it, and I got write error messages. I tried rebooting the computer (it hard locked up). My drive made a screeching noise, a couple clicks, and it was not detected during POST. I tried a few more times, no go. So I gave up and walked away. I looked in to the RMA process, and saw that Seagate claims 40% of their drives are 'fine' when they get there. Mine was dead... I was sure of that.

The next day I was ready to RMA the drive (it's 8 months old). Just for grins I powered up the machine. Spun up and booted Ubuntu just fine. I noticed the fan on the side of the case was jammed with a ribbon cable (it's a low profile microATX case) - probably from when I'd futzed with the DVD drive the day before. Ah hah. I moved the ribbon cable, the fan spun up, and... all has been well ever since. No problems with the drive.

I learned a few things though. I learned about hddtemp, the program to monitor your hard disk temperature (the disk runs normally at ~37C). I also learned that these drives are a lot more temperature sensitive than I thought... and they might give you a second chance if they over heat.

---

