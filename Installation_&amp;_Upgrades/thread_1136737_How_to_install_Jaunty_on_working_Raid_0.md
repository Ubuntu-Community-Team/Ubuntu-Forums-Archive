---
title: "How to install Jaunty on working Raid 0 ?"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by astronaute on 2009-04-25
Hello,

My system:
MB: Asus P5E3 Deluxe
Raid 0 - 2x36 GB - WD Raptors [system]
Raid 1 - 2x500 GB [storage]

Actually the Raid is configured in BIOS and working (XP 64 installed).

I would like to install the new Jaunty 9.04 on Raid 0 [system] but partioner treat them as separate disks and tells me that there is no OS installed on it, it scares me :)

Am I doing something wrong, or it's not possible to install it this way ?

Please help me as I really want to move away from Windows :)

(I am not a Linux leet, but know how to deal with Debian and Ubuntu if it does not involve advanced and risky manipulations)

Thank you in advance !

---

### Post by astronaute on 2009-04-25
Ok, little update.

I downloaded and installed the Alternate 64bit cd, and this time the partioner asked me if I wanted to activate SATA Raid disks. 

But on the next screen it shows no disks at all, empty list :(

So if you have same problem, don't download this particular alternate version, as it is of no help. Ubuntu doesn't like my system at all. I'll stick to windows until I can actually install it on my system.

Thank you for reading, I suppose I am unlucky :)

Cheers.

---

### Post by rgenoud on 2009-04-25
> **astronaute said:**
> 
My system:
MB: Asus P5E3 Deluxe
Raid 0 - 2x36 GB - WD Raptors [system]
Raid 1 - 2x500 GB [storage]
Actually the Raid is configured in BIOS and working (XP 64 installed).

I would like to install the new Jaunty 9.04 on Raid 0 [system] but partioner treat them as separate disks and tells me that there is no OS installed on it, it scares me :)


Hi!
The raid system on your motherboard is not an hardware raid, so the OS needs a driver to recognize the raid array.
As far as I know, there's no such driver for ubuntu. In fact, this kind of raid isn't really better than pure software raid (the one that is proposed on the alternate install CD).
So, if you want something like a dual boot windows/linux on your raid 0 array, there's no easy solution (beside write the Intel matrix storage driver for linux...).

The only safe and easy way to make a dual boot windows/linux on the same raid array would be to have an hardware raid card. (you can recognize them by their price (for example : Promise SuperTrak EX12350).
With these cards, the OS really sees only one disk, and the perfs are far better.

What I would recommand is:
- erase everything on your HDDs
- don't use the raid in the bios
- install ubuntu (with alternate), and make the software raid arrays like you want.
- if you really want windows, install it on a virtual machine (vmplayer for example).

on the other hand, if you don't wanna loose your week-end re-installing windows, just install ubuntu in a virtual machine (vmx builder or easy vmx can help you creating the machine's config file).

richard.

---

### Post by rgenoud on 2009-04-25
ok, my bad, my answer was maybe a little to spontaneous...
It seems to be possible to install windows and ubuntu on a fake-raid array:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ubuntuforums.org/showthread.php?t=464758](http://ubuntuforums.org/showthread.php?t=464758)
[http://ohioloco.ubuntuforums.org/showthread.php?t=630644](http://ohioloco.ubuntuforums.org/showthread.php?t=630644)

good luck, and don't forget to backup your disks... ;)

---

### Post by astronaute on 2009-04-26
> **rgenoud said:**
> ok, my bad, my answer was maybe a little to spontaneous...
It seems to be possible to install windows and ubuntu on a fake-raid array:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ubuntuforums.org/showthread.php?t=464758](http://ubuntuforums.org/showthread.php?t=464758)
[http://ohioloco.ubuntuforums.org/showthread.php?t=630644](http://ohioloco.ubuntuforums.org/showthread.php?t=630644)

good luck, and don't forget to backup your disks... ;)


Hello and thank you for your time :)

I already tried to boot on alternate cd (my 2nd comment) but it does not see my drives, and unfortunately, I want to use my windows for gaming and linux for work, so VM is not an option as I really need both OS to be performant.

[B][https://wiki.ubuntu.com/WubiGuide#Software%20raid%20arrays](https://wiki.ubuntu.com/WubiGuide#Software%20raid%20arrays)

[/B]Maybe I should try wubi install ? Are soft Raids supported in Jaunty ?

---

### Post by rgenoud on 2009-04-26
yes, the software raids are supported in jaunty (my jaunty is installed on a raid1 array).

have you tried the command:
sudo dmraid -s

to see if you array is detected or not ?
(you can grab a console during alternate-cd install with alt-F2 (or F3, or F4... I don't remember).
you should see something like this:
*** Active Set
name   : nvidia_dgicebef
size   : 488397056
stride : 128
type   : mirror
status : ok
subsets: 0
devs   : 2
spares : 0

---

### Post by astronaute on 2009-04-27
Okay so :

[IMG]http://img15.imageshack.us/img15/2343/img0690j.jpg[/IMG]

I choose yes, and it show me an empty list :

[IMG]http://img23.imageshack.us/img23/328/img0691g.jpg[/IMG]


dmraid -s

[IMG]http://img17.imageshack.us/img17/1825/img0688d.jpg[/IMG]

---

### Post by bokkie on 2009-04-27
Same thing happened to me with Intel's Rapid Recovery (Raid 1) and the Jaunty alternate install disk.  

I have Windows XP up and running on this setup.  

Was able to install Jaunty from the desktop version. It recognized the WinXP partition OK but not the RAID, so it installed only onto one disk.  I then used the WinXP to update the mirror.  After that I had GRUB on both members of the RAID, and I could remove either one and still boot off the other. 

However, I also tried to install Jaunty from the alternate install disk.  That did not recognize the WinXP partition, and gave the same blank list.

I then tried to activate dmraid at the command prompt (after the installer has detected the presence of the RAID): dmraid -a y

That worked, because the partitioner now recognized it, but it still did not see the WinXP partition on the RAID at all.  It seems there must be a workaround for this, but I have no clue.

---

### Post by rgenoud on 2009-04-27
ok, so there's may be a problem with jaunty.
maybe you can try with intrepid and/or hardy alternates they might not have this problem.
(and you could upgrade to jaunty after installation...)

---

### Post by WIGGMPk on 2009-05-25
@ astronaute

What is the full name of your Volume ID?

I ask because I was having exactly the same problem with my fakeraid setup. I was using the Intel whatever Matrix crap. I have an ASUS G50Vt and the Vista recovery disc's could see and install to the raid fine.. (just a simple Raid0 with 320GBx2 HD's)

My Volume ID was "Mobile Raid" and for some unknown reason I tried one last time, and changed the volume ID to "Mobile-Raid" and Jaunty picked it up fine.. I think it might be an issue with its ability to recognize the space in the Volume ID..

However.... Very unlikely and I prolly just got lucky.

Good Luck..

---

### Post by kaptoxic on 2009-09-11
Hi,
I've tried to install Ubuntu 9.04 (alternate Jaunty CD) and have encountered the same problem - after pop-up about detecting SATA RAID, partitioner can't see the RAID-0 array.

Configuration:
Asus P5Q Deluxe, Intel e8500
2x36 raptor - 4 partitions created with winXP, one has running XP installation
1x160GB ATA drive

astronaute, have you managed to solve the problem? If you did, please reply how!!!
If anyone have some advices, I would be glad to hear them out!

Kind regards,
Ivan

---

### Post by ronparent on 2009-09-11
To all: Try using the install to raid steps layed out on this site: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

It has been updated for use on jaunty.

---

### Post by kaptoxic on 2009-09-23
> **ronparent said:**
> To all: Try using the install to raid steps layed out on this site: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

It has been updated for use on jaunty.
I've tried that, followed the steps and...
> **kaptoxic said:**
> after pop-up about detecting SATA RAID, partitioner can't see the RAID-0 array.
any ideas? I've heard Suse has no this kind of problems... But I would really like to try Ubuntu... :?

---

### Post by Lucretius on 2009-09-25
I have the same issue...

Using a nforce-2 based board with a built in promise "raid" controller.

I have to use this controller to recognize my sata drive.

I managed to get intrepid to install fine... however jaunty and karmic both fail to see the drive.

I know it CAN work... because I have had ubuntu on this machine before.

Any suggestions guys?

---

### Post by kaptoxic on 2010-02-03
Has anyone solved this problem? :)

---

