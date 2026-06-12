---
title: "[SOLVED] Can't Boot from SATA"
date: 2008-12-04
forum: Hardware
---

### Post by BassKozz on 2008-12-04
This is a continuation of this thread: [http://ubuntuforums.org/showthread.php?t=1000143](http://ubuntuforums.org/showthread.php?t=1000143)

**I am unable to install and boot from my SATA drives, but Ubuntu has no problem installing and booting from IDE.**

_My setup:_
**MoBo:** [Intel D865GBF Desktop Board]("http://www.intel.com/support/motherboards/desktop/D865GBF/")
**CPU:** P4 3.0Ghz
**RAM:** 4x1GB G.Skill Sticks
**VIDEO:** FX5200 AGP card
**IDE1:** Seagate 250GB (ST380013A)
**IDE2:** Maxtor 250GB (Diamond Max Plus9)
**SATA1:** Western Digital 320GB (WD3200JD-22KLB0)
**SATA2:** Seagate 200GB (ST300822AS) - ******UBUNTU INSTALLED ON THIS ONE******

When ever I try and install Intrepid or Hardy on my SATA2 drive the install goes fine but upon reboot all I get is a blinking cursor (no Grub or anything).  But when I install on one of my IDE drives it boots just fine.  Any idea's on why Ubuntu won't boot from my SATA drives?

---

### Post by razy60 on 2008-12-04
How are the drives connected, in what order on the ribbons, can you install and run if only the sata drive/drives are connected.

edit:has IDE1 got a master jumper plug on and are the Ide drives connected by 40 or 80 wire ribbons?

Also i had a similar problem but only with Ide drives, i eventually tried a version of Ubuntu called ultimate edition 2.0 which uses 8.10, just uninstall anything you don't need(its bloated with pre installed progs), which installed fine.
 only thing i could see that was different about the install was that it needs a dvd as it is 1.6gig as opposed to 600mb that is the normal 8.10.

Raz

---

### Post by caljohnsmith on 2008-12-04
So you mentioned something in the other thread about using a RAID 5 controller? Unfortunately, it is not uncommon that:
```
Ubuntu + RAID = Problems

```
Have you checked out this tutorial yet:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Maybe that will help. Also, please open a terminal (Applications > Accessories > Terminal) and post:
```
sudo fdisk -lu
```
So we can get an idea how Ubuntu sees your drives.

---

### Post by BassKozz on 2008-12-04
> **razy60 said:**
> How are the drives connected, in what order on the ribbons, can you install and run if only the sata drive/drives are connected.
The drives are plugged in in the same order as shown in my original post:> **IDE1:** Seagate 250GB (ST380013A)
**IDE2:** Maxtor 250GB (Diamond Max Plus9)
**SATA1:** Western Digital 320GB (WD3200JD-22KLB0)
**SATA2:** Seagate 200GB (ST300822AS) - ******UBUNTU INSTALLED ON THIS ONE******
> **razy60 said:**
> 
edit:has IDE1 got a master jumper plug on and are the Ide drives connected by 40 or 80 wire ribbons?
Both IDE drives have "Cable Select" jumper on.
Both IDE drives are connected to 80wire ribbons.
> **razy60 said:**
> 
Also i had a similar problem but only with Ide drives, i eventually tried a version of Ubuntu called ultimate edition 2.0 which uses 8.10, just uninstall anything you don't need(its bloated with pre installed progs), which installed fine.
 only thing i could see that was different about the install was that it needs a dvd as it is 1.6gig as opposed to 600mb that is the normal 8.10.

Raz
I'd rather stick with the Vanilla Ubuntu.
Thanks for the suggestion thou.
> **caljohnsmith said:**
> So you mentioned something in the other thread about using a RAID 5 controller? Unfortunately, it is not uncommon that:
```
Ubuntu + RAID = Problems

```
Have you checked out this tutorial yet:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

I never said anything about RAID controller... My intention is to setup a Software RAID array (mdadm) using IDE1+IDE2+SATA1 once I can get Ubuntu installed and booting on my SATA2 drive, but there is no controller installed all of the drivers are directly connected to the MoBo.
> **caljohnsmith said:**
> 
Maybe that will help. Also, please open a terminal (Applications > Accessories > Terminal) and post:
```
sudo fdisk -lu
```
So we can get an idea how Ubuntu sees your drives.
Will report back this the results of "sudo fdisk -lu" in 1 Minute.

---

### Post by BassKozz on 2008-12-04
Results of "sudo fdisk -lu" from Hardy LIVE BootCD
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000e3ea

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0001a59a

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0005dadf

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00054205

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd2       374796450   390716864     7960207+   5  Extended
/dev/sdd5       374796513   390716864     7960176   82  Linux swap / Solaris

```

Thanks for your help **caljohnsmith**

---

### Post by razy60 on 2008-12-04
Will 8.10 install and run if you only have one sata drive connected, in other words completely disconnect all other drives except the sata drive you want to install on.
On the sata ribbon is 2 the second or first drive from the mobo.

Raz

---

### Post by BassKozz on 2008-12-04
> **razy60 said:**
> Will 8.10 install and run if you only have one sata drive connected, in other words completely disconnect all other drives except the sata drive you want to install on.
I removed all the other HD's and booted and I got the same problem (blinking cursor).  I then installed Hardy again (using "Guided - use entire disk") rebooted and...
**[SIZE="4"]It worked !!![/SIZE]** =D>

Now to reconnect the 3 other drives and see if it still boots... I will post back in a few with my results...
> **razy60 said:**
> 
On the sata ribbon is 2 the second or first drive from the mobo.

Raz
SATA1 is connected to the first sata ribbon coming from the mobo
and
SATA2 is connected to the second sata ribbon coming from the mobo

---

### Post by BassKozz on 2008-12-04
I just reconnected all the drives and **IT'S WORKING** !!!
Thanks for all the help **razy60** & **caljohnsmith**.):P

---

### Post by razy60 on 2008-12-04
if i remember correctly your master boot device needs to be on the first connection from the mobo, also have you got the latest BIOS update  for your board there is another post on here where they had a problem until they did the update.


Raz

YeeeHa

---

### Post by BassKozz on 2008-12-04
> **razy60 said:**
> if i remember correctly your master boot device needs to be on the first connection from the mobo, 
Well it seems to be working fine now even thou it's connected to the 2nd SATA port on the MoBo.
> **razy60 said:**
> 
also have you got the latest BIOS update  for your board there is another post on here where they had a problem until they did the update.


Raz

YeeeHa
The BIOS version on my board is **P24** the latest version is **P25** but after reviewing the release notes for P25:
> **New Fixes/Features:**
[LIST]
[*]Updated VBios to Build 1235.
[*]Fixed and issue of not defaulting video to the proprietary video card.
[*]Fixed and issue of POST code D0 hang when proprietary video card is installed and CMOS is corrupt.
[/LIST]
It doesn't sound like anything that pertains to my problems so I'd rather not flash (flashing BIOS scares me :p )
Although I don't know what the updated VBios does?

Anyways, Thanks for all your help Raz, You :guitar:

---

### Post by BassKozz on 2008-12-05
I've got another update, 
There is a setting in my MoBo's BIOS that sets the HD boot order, obviously I set the 200GB SATA2 to the top of the list, but what I didn't realize was that I could remove the 3 other drives from the boot order all together which once I did that there was no problem installing and booting to the SATA2 drive... So there really was no need to disconnect the other drives it was just a matter of removing them from the boot order list.

---

