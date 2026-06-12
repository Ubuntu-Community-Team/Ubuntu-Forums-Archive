---
title: "dmraid won't detect Intel FakeRAID?"
date: 2009-05-10
forum: Installation &amp; Upgrades
---

### Post by Pateris on 2009-05-10
I'm trying to get my Jaunty install to detect my Intel ICH9R fakeRAID 0.

when I do this:
```
morgan@office-pc:/$ sudo dmraid -ay
ERROR: isw device for volume "FastRAID" broken on /dev/sdc in RAID set "isw_bjcgabcccc_FastRAID"
ERROR: isw: wrong # of devices in RAID set "isw_bjcgabcccc_FastRAID" [1/2] on /dev/sdc
ERROR: isw device for volume "FastRAID" broken on /dev/sdb in RAID set "isw_hfjaidbdf_FastRAID"
ERROR: isw: wrong # of devices in RAID set "isw_hfjaidbdf_FastRAID" [1/2] on /dev/sdb
RAID set "isw_bjcgabcccc_FastRAID" was not activated
RAID set "isw_hfjaidbdf_FastRAID" was not activated
```As you can see, this doesn't work.  /dev/mapper is empty, except for a file called **control**.  Don't know what that does.  

**EDIT**: [COLOR=Red]I am suspicious the problem lies in the fact that dmraid thinks each disk in the RAID is a separate array - thus isw_bjcgabcccc_FastRAID and isw_hfjaidbdf_FastRAID.

Is there a way to get dmraid to fix that?  or fdisk?  Or something?[/COLOR]

---

### Post by Skinner_au on 2009-09-06
I'm having exactly the same problem on 8.10... I was considering upgrading to 9.04 to see if that would fix it... apparently not.

My suspicions on the problem are the same, I just don't know where to begin to fix it...

Any takers on a solution?

thx

Sk

---

### Post by charkear on 2010-12-19
I am having this same problem on 10.10

dmraid detects my raid 10 array as a raid 1 array with two extra discs.

---

### Post by Quackers on 2010-12-20
As far as I'm aware Intel raid and dmraid are completely different animals. Ubuntu won't recognise the Intel raid - it just sees 2 discs (at least in raid0 ). To use dmraid you need to delete the Intel raid array and start again. This means that you will lose your current system if you are on raid0 - not sure about raid1.

---

### Post by ronparent on 2010-12-20
If you do 'dmraid -l' you will discover that dmraid supports the intel chipset for raid 01 but not raid 10. I have seen this before where not all the levels supported by the Windows driver are supported by dmraid.

---

