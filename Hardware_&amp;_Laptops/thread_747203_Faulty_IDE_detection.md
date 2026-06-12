---
title: "Faulty IDE detection"
date: 2008-04-06
forum: Hardware &amp; Laptops
---

### Post by D1SoveR on 2008-04-06
First of all, I'd like to greet the whole Ubuntu community, since it is my first post here.

I'm having a little bit of a problem with installing Ubuntu on my newly-built PC. Here's the story:
I had an old PC (Athlon XP 1700+, 256 MB RAM with two [80GB Seagate HDDs]("http://www.seagate.com/support/disc/specs/ata/st380011a.html")). Ubuntu 7.10 was
installed on that PC for some time, but I decided to go back to Windows XP (didn't have enough
free time to learn how to handle the system).

Recently, I bought an incomplete Intel-based PC. I've managed to build two working PCs by using
some spare parts I had left after my previous PC broke. New PC consists of [MS-6728 MSI motherboard]("http://global.msi.com.tw/index.php?func=proddesc&prod_no=569"),
Pentium 4 2.60GHz (Northwood), 2GB Kingston DDR SDRAM, Radeon 7500, one 80GB Seagate HDD
(taken from the other PC) and HP DVD Writer. Motherboard seems to be slightly damaged - nothing
connected to second IDE channel shows up, so I have both HDD and DVD on first IDE channel. It has
some trouble with these devices (boot-up initialization lasts for about 30 seconds), but Windows XP works
just fine, detecting both HDD and DVD.

The problem starts when I try to install Ubuntu. I went through 3 Live CDs (Ubuntu 7.10, Ubuntu 7.10 PL
and Kubuntu 7.10) and none of these CDs were able to boot Linux. Everytime I tried to run it (be it graphical mode,
safe-graphical mode, checking CD for defects), I ended up in ash shell.
Then I tried Ubuntu 7.10 Alternate CD. During installation it gave me the error message about not being
able to find CD-ROM. When I logged to the second console (using Alt+F2), I did "ls | more" command in
/dev directory just to discover there were no /hda or /cdrom entries at all. When I plug out one of the devices
(either DVD or HDD), I don't have that pause during boot-up and (if I plugged out HDD) I'm able to run Ubuntu Live CD,
but, when both are plugged in, Ubuntu doesn't see either of them.

Just to be sure, I decided to boot from GParted Live CD (based on Gentoo Linux with kernel version 2.6.21-gentoo-rc2)
and, much to my surprise, it had no trouble detecting both HDD and DVD (GParted was able to see the disk and there were
/hda and /cdrom entries in /dev directory (checked through the console).
HDD is in good condition (ran every kind of test before moving it to another PC), same for DVD (I was able to both
read and write CDs on the new PC under Windows), RAM was tested too.

My two questions are:
1. Is it a common problem / Has anyone on the forum experienced something like that?
2. Was anyone on the forum able to get around the faulty IDE detection during installation?

---

### Post by softtower on 2008-04-06
I never heard of such symptoms before, but just yesterday someone on #ubuntu IRC was asking the exact same question. (was it you? :-))

I would go into your motherboard BIOS and try flipping ATA/SATA settings, some BIOSes have "SATA mode" that you can tweak. My older ThinkPad had issues with that (didn't see it's own hard drive).

---

### Post by D1SoveR on 2008-04-07
No, actually, it wasn't me on the #Ubuntu IRC channel.
Indeed, the BIOS on my motherboard has some options used to configure SATA.
The problem is, I've tried every possible option and still I got same results - the 30-second
pause during initialization and Ubuntu not being able to detect any device on IDE. As far as
I know, code responsible for handling IDE devices is built into kernel, right? Maybe the problem
is caused by some Ubuntu-specific modifications? I'm running Gentoo LiveCD now and it doesn't
seem to have any problems detecting IDE devices (though I had some hard time making the X Server
work, since the drivers for my Radeon were apparently not included). Is there a way to replace
the part responsible for IDE detection on LiveCD or something? Because it's either that or I'm installing
Gentoo. :-)

---

