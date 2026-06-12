---
title: "Grub Problem After Installing 2nd SATA Hard Drive"
date: 2010-04-18
forum: Hardware
---

### Post by gspira on 2010-04-18
I'm running a dual boot  Ubuntu/Win Vista system and I'm trying to install a 2nd sata hard drive.  When I install the 2nd hard drive, I'm running into a Grub Error 5 preventing the computer from booting up at all.  If I unplug the data cable from the 2nd drive, the computer goes back to booting fine.

I got the same error in my previous attempt to install a hard drive, but I quickly found that that drive was defective by looking at the bios and seeing that the bios couldn't identify the name of that drive or its correct size.  This time, the bios has no problem dealing with the new drive when its plugged in, so the drive itself appears to be ok.

At this point I don't have a clue as to what the problem could be or what I should do.  I'm not a linux expert by any means, so I definitely could be missing something major.  I would appreciate any help I can get.

---

### Post by buntudawg on 2010-04-18
Hi.

Have you checked the jumper settings on the drives. This error can occur if the second drive is not set as slave.

---

### Post by coffeecat on 2010-04-18
> **buntudawg said:**
> Have you checked the jumper settings on the drives. This error can occur if the second drive is not set as slave.

The OP is using a SATA drive, so jumper settings should be immaterial.

@gspira, since you are getting a numerical grub error, I assume you are using a version of Ubuntu with legacy grub. Is that so? Which version of Ubuntu and which version of grub?

Assuming you are using legacy grub, the [grub manual]("http://www.gnu.org/software/grub/manual/grub.html#Stage2-errors") lists error 5 as:

> 5 : Partition table invalid or corrupt
This error is  returned if the sanity checks on the integrity of the partition table fail. This is a bad sign.... which is interesting. Clearly the partition table on your main system drive is OK, since you can boot up with it, so this must refer to the partition table on the new drive. I guess, therefore, that this is a brand new drive which has not yet been "initialised" (by creating a partition table). Is that so? If yes, that might explain the problem. However, if all your system is on the first drive, I would have thought it would have booted up from that and simply ignored the drive with no partition table. Or not - I don't know.

Next question: Is the first drive (sda - with your system) plugged into the first SATA port on the motherboard, and are you plugging the new drive into the second port?

The only other thing I can suggest is to boot up from a live CD with the new drive attached, go into Gparted and create a partition table from Device > Create Partition Table. Then you could create whatever partitions you need.

Alternatively, if you have an external USB SATA enclosure, and you have Gparted installed on your system, you could put the drive in the enclosure and create a partition table with Gparted from your system.

Once you've got a partition table established, try refitting the drive and booting up.

---

### Post by buntudawg on 2010-04-18
> The OP is using a SATA drive, so jumper settings should be immaterial.

OMG! I must have been miles away.

Sorry for useless input gspira.

Thanx coffecat for pulling this one up.

---

### Post by gspira on 2010-04-18
----------------
@gspira, since you are getting a numerical grub error, I assume you are using a version of Ubuntu with legacy grub. Is that so? Which version of Ubuntu and which version of grub?
----------------

I'm using the current beta of Ubuntu 10.04.  I'm pretty sure that I could swear that I installed grub 2.0 about 6 months back, but that doesn't seem to make much sense given what you say. I'm not sure how to check which grub I'm running.


-------------------
... which is interesting. Clearly the partition table on your main system drive is OK, since you can boot up with it, so this must refer to the partition table on the new drive. I guess, therefore, that this is a brand new drive which has not yet been "initialised" (by creating a partition table). Is that so? If yes, that might explain the problem. However, if all your system is on the first drive, I would have thought it would have booted up from that and simply ignored the drive with no partition table. Or not - I don't know.
-------------------------------

Yes, the new drive has indeed not been initialized.

------------------------------
Next question: Is the first drive (sda - with your system) plugged into the first SATA port on the motherboard, and are you plugging the new drive into the second port?
----------------

I'm not sure how to count first and second ports - I know where all the ports are and where everything is plugged in, just not the numbering.  But the first drive is plugged into where the manufacturer plugged it into, which is the "outlet" to left of where I plugged the second drive into, and in the bios the older drive is listed above the newer drive.  So, I'd be really, really surprised was trying to use the new hard drive to boot with.


------------------
The only other thing I can suggest is to boot up from a live CD with the new drive attached, go into Gparted and create a partition table from Device > Create Partition Table. Then you could create whatever partitions you need.
-------------------

I guess that just checking to see if I can indeed boot up from a live cd will tell me something.  If I can't, this will be even stranger.

Thanks,
Greg

---

### Post by coffeecat on 2010-04-18
> **gspira said:**
> I'm using the current beta of Ubuntu 10.04.  I'm pretty sure that I could swear that I installed grub 2.0 about 6 months back, but that doesn't seem to make much sense given what you say. I'm not sure how to check which grub I'm running.

From my limited experience of grub 2 error messages (because I haven't had many errors yet with grub2) I thought that they didn't have error numbers, which is why I assumed that grub error 5 is from legacy grub. But it doesn't matter anyway whether you've got grub 2 or legacy. This is unlikely to be a grub problem. Grub is merely grumbling about another problem.

> **gspira said:**
> Yes, the new drive has indeed not been initialized.

OK. That explains the grub error message.

> **gspira said:**
> I'm not sure how to count first and second ports - I know where all the ports are and where everything is plugged in, just not the numbering.  But the first drive is plugged into where the manufacturer plugged it into, which is the "outlet" to left of where I plugged the second drive into, and in the bios the older drive is listed above the newer drive.  So, I'd be really, really surprised was trying to use the new hard drive to boot with.

Good point. The BIOS should list the primary drive first - which it seems to be. If you want to be sure, most motherboards label the SATA headers - except that the labels tend to be small. Try shining a light on that area to see whether they are labelled.

> **gspira said:**
> I guess that just checking to see if I can indeed boot up from a live cd will tell me something.

Yes, but more importantly trying to boot up from a live CD will enable you to create a partition table on the new drive - hopefully. The live CD doesn't use grub - it uses isolinux - so *hopefully* it won't be upset by the lack of a partition table on the secondary drive and will boot OK.

---

