---
title: "Trials of an extreme noob:  Grub won't load WinXP Pro on dual-boot system."
date: 2005-09-09
forum: Hardware &amp; Laptops
---

### Post by whisperx on 2005-09-09
Hi all, I'm completely new here and also a total linux n00b.  However, I see all the great support this community seems to offer and I'm really interested in learning a lot.  I'm trying to set up a dual boot system so that I can use WinXP when I need to get stuff done, and use linux when I have the time to learn and have fun.  At some point, perhaps I will be able to use linux more and windows less...

Here's my setup:  I have WinXP Pro installed on an 80gb SATA hdd (single ntfs partition).  I also have an 80gb IDE hdd on which I've always kept ~7gb as unpartitioned space, and the remainder as a logical windows ntfs partition for file/backup storage.  Yesterday, I decided to install ubuntu using the 7gb of free space on the IDE drive.  I chose to use Grub when given the option during installation.

Here's the problem:  After the ubuntu installation was complete, the system rebooted and went into ubuntu no problem.  On next reboot, I decided to go into WinXP to make sure everything was kosher there.  WinXP Pro was listed as an option under Grub, but when I selected it, no dice.  Here's the error I got :?:

root (hd1,0)
Filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1

What I did:  After a while,  I really just wanted to get back into Windows to finish up some stuff I was doing, so I opened up my box and physically disconnected my IDE drive.  That seemed to solve the WinXP problem, as I was then able to boot right up into Windows as usual.  Of course, I could no longer access the files on my IDE drive because it was disconnected.  Sadly, to solve this problem, I hastily used the partition manager on my WinXP installation CD to simply delete my ubuntu partition from my IDE drive:(  But at least everything was back to normal.

I would like to give this a try again, of course, but could use a couple pointers.  Why would Grub be unable to load my WinXP Pro OS if it was listed as a selection?  Is it because it's installed on a SATA drive (as opposed to IDE)?  What would happen if I chose not to use Grub during the ubuntu installation?  I'd like to install again but would obviously like to have a simple way when I boot up to select which OS I want to load...

Sorry for this incredibly noob like question.  As time goes on I hope to have more exciting topics to post ;-)

---

### Post by amohanty on 2005-09-09
Usually the source of problems like these is the way the drives are setup in the BIOS. Make sure that in your CMOS setup both drives are setup as auto, and that the boot order has the SATA drive as the primary boot source. Please keep in mind that some BIOS's recognize SATA drives as removable devices.

HTH
AM

---

### Post by grimdeath on 2005-09-10
ok, im only 2 weeks into learning myself, but here's a bit of advice from "experience" lol

im running a dual boot with 2 hard drives and i was getting the same problem, for whatever reason its recommended that your windows partition be setup on the first partition of the first hard drive(seems you have this)

next i dont beleive ubuntu can use ntfs, it uses its on "type" be sure and let it make the partition itself, dont pick manually to use ntfs if you can keep from it(though i dont think this is the issue)

you may also need to check what the recommened partition size is for ubuntu cause im thinking you need about 5 gig more then what you got, BUT im not sure...there are several partition tools out there that will let you shrink you current windows partition...someone else recommend one? then enlarge your ubuntu one as needed!

i was getting the exact same problem as you mentioned but it was because i had installed windows on the second hard drive(slave) and then tried to install ubuntu on the master drive and it really didnt like that, grub didnt work correctly either! if its a possiblity backup important info on your windows drive and start fresh, maybe a half/half partition?

definatly use grub, just make sure it gives you the message during the install saying something like "detected windows os, setup dual boot" cause i beleive grub installs stuff on the windows partition so it works correctly

hope this will help you out a bit, ill check back with ya later if i can!

btw be sure and use [www.ubuntuguide.org](www.ubuntuguide.org) as soon as you get up and running :) if all else fails use a livecd!

---

### Post by whisperx on 2005-09-10
[QUOTE=amohanty]Usually the source of problems like these is the way the drives are setup in the BIOS. Make sure that in your CMOS setup both drives are setup as auto, and that the boot order has the SATA drive as the primary boot source. Please keep in mind that some BIOS's recognize SATA drives as removable devices.

HTH
AM[/QUOTE]

Here's the way I've always had it:  First boot device is floppy, second is CD-ROM, third is my SATA drive.  The IDE drive was not even included as a boot device.  In my BIOS (for ASUS A7N8X Deluxe r1.04 nForce2 mobo) SATA is recognized as fixed device.

Is it possible that Ubuntu altered my BIOS settings (I'm not sure how it would gain access to my BIOS, but maybe)?  I actually recall, now that I think of it, that after installing ubuntu and looking in my BIOS settings I saw my IDE hdd listed as primary boot device.  I definitely did not make that change myself.

---

