---
title: "[SOLVED] Onboard Raid Disk Boot Failure"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by earle79 on 2008-12-30
Ok, well not sure what i managed to screw up but something big I guess.
**System Configuration**
[COLOR="RoyalBlue"]Motherboard: *Soyo KT400 (onboard RAID HighPoint HPT 372)*
Video: *Nividia MX400??(i'll check to make sure)*
Processor: *AMD Athlon 1800*
RAM: *2GB*
HardDrive 1: *40gig Where Ubuntu Was supposedly installed.*
HardDrive 2&3: *on RAID Controller 120Gig Each **(Still NTFS i need some of those files for another machine)***
OpticalDrives: *(2)DVD-RW drives*[/COLOR]

I used alternate CD to install ubuntu 8.10, everything went good, i didnt touch the raid drives when it got to the partition section, but they were list first??  I created the partition on the 40gig drive installed, and went to reboot, and i get this message....[COLOR="Red"][SIZE="3"]**Disk Boot Failure, Please Insert System Disk And Press Enter**[/SIZE][/COLOR]

im not really sure what to do??  should i unplug my raid??  i have read that this can cause some issues??

---

### Post by earle79 on 2008-12-30
well, i turned off raid on the board, and still no boot so I decided to try reinstall with the raid off.  now istall keeps failing at 6% when installing software...so what now? i ran a check on the cd and it checks out good.  what did i do to my hard drive??

---

### Post by earle79 on 2008-12-30
anyone??

---

### Post by albinootje on 2008-12-30
> **earle79 said:**
> well, i turned off raid on the board, and still no boot so I decided to try reinstall with the raid off.  now istall keeps failing at 6% when installing software...so what now? i ran a check on the cd and it checks out good.  what did i do to my hard drive??

Can you (from the installation cdrom) post the output of :
```

sudo fdisk -l
lspci
sudo lshw -c disk -c storage -sanitize

```

---

### Post by earle79 on 2008-12-30
> **albinootje said:**
> Can you (from the installation cdrom) post the output of :
```

sudo fdisk -l
lspci
sudo lshw -c disk -c storage -sanitize

```

UMM...no cause i don't have a live version? i am using alternate cd.  unless there is a way to do that in recover mode??

also, i am burning another copy of it cause i burnt it at 8X and from what i read should have only been 4X, although ive never had that issue before any other time??

---

### Post by earle79 on 2008-12-30
well im not sure whats wrong cause i did another cd integrity check it failed, i burnt another cd did a check and it failed. maybe my iso is bad?

Iso checksum checked good....i had a linuxmint Live cd laying there and it will load to the desktop but when i try to install the step were you choose the partitions is blank, there is nothing to choose from???what the heck is going on here......i see the 40gb drive in the file system.im confused

---

### Post by albinootje on 2008-12-31
> **earle79 said:**
>  i had a linuxmint Live cd laying there and it will load to the desktop but when i try to install the step were you choose the partitions is blank, there is nothing to choose from???what the heck is going on here......i see the 40gb drive in the file system.im confused

Perhaps you have a fakeRAID in your computer, see here :
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by earle79 on 2008-12-31
ahh, yes you are right.  but i do have it working now.  i had to load the live cd, us gparted and tag my drive for boot, i guess it never got tagged on the first install.  

once i did that, i used one of the alternate cds, even though it failed the integrity check it installed fine, until the very end of the software install, so i went back and tried again it picked up where it let off, and finished, its almost like my dvd drive feel asleep??  anyway it finished and booted right up.  works just fine.

then i installed a driver for my geforce2 card and works good, now just updating, about 205 things needed updated, holy crap!!

it was a long nite...morning, but now i will try to get the onboard raid working, and see what happens from there.

thank your for helping me. i am reading on the fakeraid and my onboard is one of those described in there, so i guess good luck to me huh?? thanks again.

---

