---
title: "Installing Ubuntu On Emachine Model #W3050"
date: 2005-12-18
forum: Installation &amp; Upgrades
---

### Post by gconn77 on 2005-12-18
Hello everyone. I have an Emachine Model #3050. Just a basic computer, it fits family's needs quite well. We are not crazy gamers, just like to surf the Internet, download music, and check our forums, and emails and such...

**Specifications** 
- AMD Sempron™ 3000+ Processor
- (512KB L2 cache, 2GHz, 333MHz FSB) 
- Microsoft® Windows® XP Home Edition 
- Includes eMachines 17" CRT (eView 17f3)
- (16" Viewable, 0.25mm dot pitch) 
- nVidia® nForce™ 2 Chipset 
- 512 MB DDR (1 x 512MB) PC2700
- Expandable to 2GB 
- 80GB HDD (7200 RPM) 1 
- 16x DVD±RW, Multi Format Double Layer 
- 8-in-1 Digital Media Manager (Secure Digital (SD), Smart Media, Compact Flash, Micro Drive, Memory Stick, Memory Stick PRO, Multimedia Card, USB 2.0) 
- nVidia® GeForce™ MX Graphics
- 64MB Shared Video Memory 
- 6-Channel AC '97 Audio 
- 10/100Mbps integrated Ethernet LAN 
- 56K ITU v.92 ready Fax/Modem 
- Standard multimedia keyboard, 2-button wheel mouse, amplified stereo speakers 
- 7 USB 2.0 (2 in front, 4 in back, 1 in Media Reader), 1 Parallel, 2 PS/2 (keyboard and mouse) 
- 14.25"H x 7.25"W x 16"D 
- 22.5 lbs (PC only, no packaging)

Its a very good computer for just the basic less demanding user. I am pleased with it.

Now my question is this:

I do not want to wreck the emachines's preformated resque files that are located on a special partitioned section on the 80 gig hard drive. The special partitioned section is FAT32 and has all the recovery info... including the Windows OS.... the remainder of the hard drive is NTFS....

How can I install Ubuntu along side with cobranded emachine version of Windows XP without screwing up too much of the computer's original factory configuration?

---

### Post by Darkhack on 2005-12-18
All you would have to do is defrag windows and then resize your NTFS partition.  With the free space you can format it as ext3 or whatever format you want that Ubuntu can handle.  All you have to do is not alter the FAT32 recovery partition.  Just in case you've never done a Linux install before, be sure to select "expert install" or mode or whatever.  Don't let the word expert scare you.  All it means is that you can alter your partitions rather than let Ubuntu do it for you (which of course Ubuntu would more likely than not, mess you up).

Also, even if you aren't installing linux... PLEASE do your self a favor and backup that recovery partition.  I own an emachines and they come with a tool that lets you make backup CD's incase the hard drive goes kurplunk.  Hell, my emachines even came with the blank CD's for me to do it with.  Look under your Start menu in program files.  Look for "system recovery" and you'll see a "Recovery Media Creator".  It will guide you through the processe of putting the recovery on to CDs.

---

### Post by azteech on 2005-12-18
I too have an emachine, which I bought second hand. The previous owner apparently wiped out the protected emachine recovery software partition.

I contacted eMachine about obtaining the software; I was told I had up to one year from date of when I bought it to purchase a complete set of recovery disks from them for approx. $20+s/h.

This can also be a solution for you, if something were to happen to the partition when you do the install, or if you really want to use the entire HD potential.

---

### Post by Ptero-4 on 2005-12-18
MAKE THE RECOVERY CD's first. The rescue partition in those PC's is known to have a self-destruct program that gets trigered by the precense of non-M$ type partitions. I know b/c I have seen tens of those in all sort of different brands and models do the same when a Linux or BeOS have been installed be it standalone or next to Windoze. That program is AFAIK some sort of way to deter users from installing non-M$ OS's on those "cheap" computers. That's one reason I prefer Mac's b/c I can put Linux or BeOS next to MacOS or replacing it w/o worrying that the machine will do something nasty b/c I attempted to replace it's native OS.

---

### Post by Darkhack on 2005-12-18
Interesting.  I've heard of some companies doing things like that before.  I have an HP computer that no longer installs a copy of office that came with it since putting Linux on it.  Now it only installs the base Windows system and thats it during recovery.  And yes it DID come with Office on the recovery CD... this was  way back when Office 97 was the norm and more computers came with office back then than they do now.  I havn't seen a computer that actually came with office in years actually.

My current emachines which is only a few months old has had Linux on it and I havn't had any problems with the partition yet.  It may have changed since Gateway bought emachines and that problem no longer occurs.  Or I could be wrong and maybe it just hasn't happened to me yet, but it seems fine on my end.

---

### Post by jenco on 2005-12-19
my compaq had a program that let you make cd's out of the partition. So you could free up that space so might wanna check that out. =)

---

### Post by gconn77 on 2005-12-20
Ok guys... thanks for the awsome feedback... my next question based off the info that is being told to me here is this:

Could I just go to the store and purchase a seperate hard drive and install Ubuntu on that? That way Ubuntu will not be on the same drive as Emachines' WIndows??? Would that be a solution to preventing the chance that the Emachine software detects the foreign operating system?

If so, then what is the process to get the computer to finally dual boot? Windows would be NTFS on C: the back up recovery is D: on Fat 32 which is partitioned on the drive number 1 which is also shared with the partitioned NTFS that carries the Windows... and then ubuntu would be on a seperate drive.... probably E... or whatever...

---

### Post by newuser111 on 2005-12-21
my computer also has a rescue partition (fat32) at the beginning of the harddrive, if you use a graphical partition manager like partition magic or qparted you can see this, just defrag and resize your ntfs partition and let ubuntu create a swap and ext3 out of the free space

---

### Post by Ptero-4 on 2006-02-01
gconn77. You may have some luck with using a 2nd drive. But I wouldn't hope too much. My sister used to have a HP Pavilion and installing linux would delete the recovery partition EVEN if I installed Linux in a 2nd HD. AFAIK in some models the program that do the censoring and deletion is more advanced and insidious than in others. It all depend on brand and model of PC and specially brand and model of BIOS/mainboard. My sister fortunatelly no longer have that $PC anymore. She's happily using a PowerMac G3 that a friend gave me and to say this, that machine serves my sister very well with ubuntu and she likes gnome alot.

---

