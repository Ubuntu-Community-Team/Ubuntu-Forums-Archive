---
title: "Bizarre Root / behaviour"
date: 2009-05-25
forum: Installation &amp; Upgrades
---

### Post by VastOne on 2009-05-25
I needed to expand my / system in order to create kernels.  I booted to my live CD and successfully shrunk my drive and did a copy and paste to expand my / partition. 

But now I can no longer do anything to my root files.  If I try to edit my menu.lst, it saves correctly but does not work, meaning the edit never happens. Even though my menu.lst shows several new entries, they never make it to grub.  It looks as if there is a rights issue or a ghost system somewhere...

This is what my disk looks like now

sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005dc84

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         608     4883728+  83  Linux
/dev/sda2             609      121601   971876272+   5  Extended
/dev/sda5             609         851     1951866   82  Linux swap / Solaris
/dev/sda6             852        5714    39062016   83  Linux
/dev/sda7           14737      121601   858393081   83  Linux
/dev/sda8            5715       14736    72469183+  83  Linux

This is what gparted is telling me:

/dev/sda1 Mounted on / Warning: Unable to read the contents of this file system!

/ dev/sd8 (where I expanded the / to) Warning Unable to find Mount Point! Unable to read the contents of this file system!

this is what grub is telling me:

find /boot/grub/stage1

 (hd0,0)
 (hd0,7)


It appears that root has lost it's security rights.  I cannot open any files for editing from Nautilus or if I drop to root from PcMan file manager. If I try to edit or open something on either of those partitions, it just hangs with the clock for 30 seconds and nothing...No events in monitor, nothing

If I open menu.lst to edit from term, it opens fine and everything saves fine. But when I boot, the changes I make never show up in grub....

I am wits end....

---

### Post by VastOne on 2009-05-25
Bump

---

### Post by presence1960 on 2009-05-25
it is forum policy that you only bump a thread after 24 hours. The nature of the beast is that sometimes we must wait until someone who knows the answer to our problem comes along. After all we all do this in our spare time. Patience is a virtue as the old saying goes.

---

### Post by VastOne on 2009-05-25
> **presence1960 said:**
> it is forum policy that you only bump a thread after 24 hours. The nature of the beast is that sometimes we must wait until someone who knows the answer to our problem comes along. After all we all do this in our spare time. Patience is a virtue as the old saying goes.

Wasn't aware of that...

All accept my apologies, please

Thanks Presence1960

---

### Post by cariboo on 2009-05-25
There really isn't a policy bout bumping, but I would suggest you read the forum [thread=885580]Do's and Don'ts[/thread].

You may want to boot from the LiveCD and run fsck on /dev/sda1 and sda8

---

### Post by presence1960 on 2009-05-25
No apology needed. Mistakes happen, that's why they put erasers on pencils. Figured you were unaware. No biggie. Hope you get an answer!

---

### Post by presence1960 on 2009-05-25
> **cariboo907 said:**
> There really isn't a policy bout bumping, but I would suggest you read the forum [thread=885580]Do's and Don'ts[/thread].

You may want to boot from the LiveCD and run fsck on /dev/sda1 and sda8

When jumping out of a plane with a parachute it is *suggested* that you pull the cord.

Just my sad attempt at humor  :D

---

### Post by VastOne on 2009-05-25
> **presence1960 said:**
> When jumping out of a plane with a parachute it is *suggested* that you pull the cord.

Just my sad attempt at humor  :D

:lolflag:

---

### Post by VastOne on 2009-05-25
> **cariboo907 said:**
> There really isn't a policy bout bumping, but I would suggest you read the forum [thread=885580]Do's and Don'ts[/thread].

You may want to boot from the LiveCD and run fsck on /dev/sda1 and sda8

Thankee Sai on both points Cariboo907

---

### Post by VastOne on 2009-05-25
> **cariboo907 said:**
> There really isn't a policy bout bumping, but I would suggest you read the forum [thread=885580]Do's and Don'ts[/thread].

You may want to boot from the LiveCD and run fsck on /dev/sda1 and sda8

Cariboo907

Running the LiveCD and running fsck -t ext4 /dev/sda1 I get the following:

fsck.ext4: Permission denied while trying to open /dev/sda6
You must have r/w access to the filesystem or be root

Same thing on sd8 and any others for that matter.

It is not mounted (verified) 

Am I missing something?

---

### Post by VastOne on 2009-05-25
> **VastOne said:**
> Cariboo907

Running the LiveCD and running fsck -t ext4 /dev/sda1 I get the following:

fsck.ext4: Permission denied while trying to open /dev/sda6
You must have r/w access to the filesystem or be root

Same thing on sd8 and any others for that matter.

It is not mounted (verified) 

Am I missing something?

Never mind.... I figured out the sudo su

Thanks

---

### Post by VastOne on 2009-05-25
running fsck reports both /dev/sda1 and /dev/sda8 are clean

This is beyond fairytale and I am begining to think a reinstall is in order...

It makes no sense how a / root filesystem can not be written to and yet I can boot to it and everything else appears to be in order....

---

### Post by VastOne on 2009-05-26
Completely removed all trace of the kernel upgrade and have edited down my menu.lst to one kernel choice but still get my original grub.  This is too much I have a headache in my eye... :shock:

---

### Post by VastOne on 2009-05-26
Solved! I had 2 drives with the same uuid that was the culprit.

Thanks for all the help and especially to Unutbu!

---

