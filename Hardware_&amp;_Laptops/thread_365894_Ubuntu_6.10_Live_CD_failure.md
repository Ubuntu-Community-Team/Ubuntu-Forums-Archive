---
title: "Ubuntu 6.10 Live CD failure"
date: 2007-02-20
forum: Hardware &amp; Laptops
---

### Post by Edgy Ed on 2007-02-20
Hello,

A newbie question.

I've done a lot of searching and found similar issues for installation but nothing with the live CD.

My problem is I boot from the Live CD and get dumped at an ASH command line.

Error reads (and this may not be completely accurate)

Unable to access tty; job control turned off

Pressing Alt F1 results in information about /root/dev/log (may be other way around) not being accessible.  Along with some other messages about things being unwriteable.  Looking in the directory the only device shown is CD ROM.

My guess is my hard disk isn't auto detected.  How do I proceed from here ?

---

### Post by tgalati4 on 2007-02-20
Dear Edge,

The Live CD really, really needs 256MB of RAM.  I recently loaded Dapper LTS (6.06.1) on an old Dell laptop with 128 MB of memory only after creating a swap partition (128 MB minimum--I used a 1 GB partition).  You can create the swap partition using the "Alternate Installation Disk".  This is a text-based installer that uses less memory to load and gets you to the partitioner so you can squish Windows into the first partition, create a generous second partition for Ubuntu (or any other Linux distro) and most importantly, a swap partition that's needed by all Live CD's.

I'm not sure why, but the Ubuntu Live CD's tend to load into the graphical operating system with an install icon.  Then you have a pick for a server (text console only) or full installation.  It would be nice to have a low-memory installer on the Grub menu, instead of downloading another ISO.

If you try to load the LIVE disk with only 128 MB then you can get the weirdness that you describe.

If you provide more details on your hardware, the community can provide more specific answers.

Best of luck,

Terry

---

### Post by Edgy Ed on 2007-02-20
Thanks for the reply.   I have enough ram. Here's some more detail about the machine.


The machine is a Sony Vaio FS 515H.  
512 MB of ram
80 gig hard disk with two equal sized partitions
The hard disk which I suspect it's not auto-detecting is a TOSHIBA MK8025GAS (according to msconfig.exe)

---

### Post by tgalati4 on 2007-02-20
Do you get dumped to a command line using the "Safe Graphics Mode"?

The next time you are at a command line report the following:
lspci
dmesg | more   (interesting parts only)
df -h                (what's mounted)
startx               (restart the X xerver)
more .xsession-errors (interesting parts only)

Your hardware is generic, except perhaps the Vaio video.  The Toshiba drive is pretty common.  When booting from the Live CD, disks are detected but not automatically mounted unless you mount them manually.  Only the swap partition is mounted (if it exists).  dmesg will show what was discovered during bootup.

It seems more like a video problem that is not allowing the xserver to start or causes it to crash soon after boot.

---

### Post by Neumahn on 2007-02-20
I am having the exact same problem.  I am using the 64 bit version and I have an AMD 64 on a Shuttle XPC with 2 gigs of RAM.  I do not want to install yet I just wanted to run it off the live CD and had the exact same error.  About once a year I get the urge to dump Microsoft and try out Linux and every year it ends the same way.  With the install not working and nobody being able to figure it out.  Then I give up and forget about it.

---

### Post by tgalati4 on 2007-02-20
That would be a dream system.  There were several Shuttles  running Lin/Freespire at the Scale 5x conference.  What other Live distros have you tried?  Try the 32-bit version first in "safe graphics mode"  I can't believe you can't get the live distro to work.  I would try 6.06 alternate install mode.  Create a swap partition and an ext3 partition, moving Windows to a smaller partition.

First clean up the Windows partition, delete extraneous cache files, etc, then do a defrag to get everything compressed.  The alternate install partitioner will safely create a partition in the free space remaining and then you can create a swap partition (1 to 4 GB is good).  What is your graphics card?

Once you get a working 32-bit version, then you can copy the vital xserver files and other goodness required when configuring the 64-bit version.

Or, buy a cheap drive and stick it in and devote it to Linux.  There are windows-based installation tools as well, but I don't have any experience with them.

Or try damn small linux (50 mb) and see if it boots into something recognizable.

---

### Post by Platinum89 on 2007-02-21
LiveCD wouldn't work for me no matter what I tried (32bit version). Tried the Alternate Install and it failed as well. So for the heck of it, I tried the 5.10 Install CD I burned. Installed with no problem and after it was finished, I ran the updates. It's running 6.06 without a problem now. I'm not sure if this will help anyone, but thought I would post it just in case.

---

### Post by Neumahn on 2007-02-21
These experiences as a user with Linux have really put me off.  I am loath Microsoft but I know when I put an installation CD in from them that it is going to work.  There seems to be a huge disconnect between the 'Linux People' and the average user.

---

### Post by tgalati4 on 2007-02-21
Dear Neumahn,
You make a valid point.  However, how many times do you have to reboot windows after installing a device driver?  When you install windows, you have to download and install device drivers which require a reboot in each case.  

Ubuntu and Linux is different in that it tries to detect as much hardware as possible before install and sometimes it fails.  To get around the failures, you have to turn off certain drivers or load an older version of Ubuntu and then upgrade through the net.  It's a pain but when you get a working system, it tends to work well.

I did a search on the forums and found that someone is selling XPC's with Ubuntu preinstalled.

Here are the specs:

    * CPU: AMD Sempron 64 3300+ (2ghz)
    * Memory: 512mb Corsair PC3200
    * Hard Drive: Western Digital 40GB SATA
    * Motherboard: Shuttle FX21
    * Graphics: Integrated VIA Unichrome Pro
    * DVD Drive: Pioneer DVD-107D DVD-RW
    * Network: Built-in 10/100mb network/Ethernet adpater
    * Floppy drive: No, but if you want one I will fit one for you

What is your motherboard?  

With dual boot, there is no reason to give up windows, you can both operating systems and choose the one that suits your computing tasks best.

---

### Post by Edgy Ed on 2007-02-22
> **tgalati4 said:**
> Do you get dumped to a command line using the "Safe Graphics Mode"?

The next time you are at a command line report the following:
lspci
dmesg | more   (interesting parts only)
df -h                (what's mounted)
startx               (restart the X xerver)
more .xsession-errors (interesting parts only)

Your hardware is generic, except perhaps the Vaio video.  The Toshiba drive is pretty common.  When booting from the Live CD, disks are detected but not automatically mounted unless you mount them manually.  Only the swap partition is mounted (if it exists).  dmesg will show what was discovered during bootup.

It seems more like a video problem that is not allowing the xserver to start or causes it to crash soon after boot.
Thanks it was the graphics.

All went well after that.

---

### Post by tgalati4 on 2007-02-22
Dear Edgy,

Please share with us what you did to get the graphics to work properly.  You are not the only one with a Viao.

Then tell us how well Ubuntu runs in day-to-day use.

The Ubuntu community welcomes your input.

---

