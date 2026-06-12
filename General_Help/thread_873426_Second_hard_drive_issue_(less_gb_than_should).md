---
title: "Second hard drive issue (less gb than should)"
date: 2008-07-29
forum: General Help
---

### Post by ruipedroca on 2008-07-29
Hi,

I'm running Hardy and I've a second hard drive that is bugging me, because it has 160gb, but only shows 33gb in gparted and in several other utils I've used.
Before, I've used that disk in a computer with a windows instalation and ntfs.
I've read around and it seems it's a mbr or grub issue.
I've tried dban and disk kill live cd's, but with no success (though maybe because of lack of knowledge).

I don't need the data in that disk, just want to be able to get back it's full capacity.

What do you recommend?


Regards,

---

### Post by forger on 2008-07-29
If it's ATA(or PATA), maybe you didn't set up the jumpers properly?

What hard drive, brand and model, do you have?
Is the hard drive partitioned as ntfs or ext3?
post back the output of:
> lspci

---

### Post by ruipedroca on 2008-07-29
This second hard drive is an Hitachi Deskstar ATA/IDE 7200rpm.
It was partitioned has ntfs, but I've tried to install kubuntu and it somehow created a ext3 33gb partition.

Like I said, I just want back it's 160gb and also I don't need it's data so there's no problem if it will be totally erased.


Here's the result of lspci:

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0e.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

---

### Post by forger on 2008-07-29
Ok, ATA, did you change the jumpers on the hard drive? There's a jumper setting to limit its hard disk size, check that it's not on that place.
(You could try removing the jumper and booting without it)

Mount your hard drive now, or if it's already mounted, I'll need you to post some more info:
```

sudo fdisk -l
sudo df -ah

```

---

### Post by derrick81787 on 2008-07-29
Is it possible that the hard drive does have the correct capacity but that you have multiple partitions?  Maybe the Kubuntu partition is 33 GB and the Windows partition is the rest.  When you installed Kubuntu, where you intending on dual booting, or were you hoping to completely erase Windows?

Can you also paste the results of the following command?
> sudo fdisk -l
I believe that should give you the size of the disk and of each partition on the disk.  However, I'm at work right now (and forced to be on Windows) so this is all from memory.


*****Edit: ** After re-reading your post, I just realized that Kubuntu is on one disk and the other is just for storage and used to have an NTFS partition on it.  However, the results of the above command could still be very useful.

---

### Post by derrick81787 on 2008-07-29
> **forger said:**
> 
Mount your hard drive now, or if it's already mounted, I'll need you to post some more info:
```

sudo fdisk -l
sudo df -ah

```

I got a phone call mid-posting and you beat me to it. Haha!

---

### Post by ruipedroca on 2008-07-30
Well, by the time I've seem this replies I've already given up and used another disk.

But, for the record, I seem to miss the jumper configurations because there's 16 different ways to put the jumpers (1 to 3 jumpers) and I've placed them in the group of 32gb limit.

However, I still believe the disk is corrupted somehow and I'll be back to this post in the near future.


Regards to all!

---

### Post by forger on 2008-07-31
Try removing all the jumpers, usually this way hard drives go by default (cable connection makes it primary or secondary).

If you think it's corrupted, you could do a low format partition using active killdisk (bootcd):
[http://www.killdisk.com/downloadfree.htm](http://www.killdisk.com/downloadfree.htm)
[http://software.lsoft.net/boot-cd-iso.zip](http://software.lsoft.net/boot-cd-iso.zip)

**[COLOR="Red"]WARNING: Select the correct device!![/COLOR]** It will erase all your data on that hard drive
Choose the "one pass fill zeros" method.

(Low level formatting of big hard drives can take more than 4-5 hours)

You can partition the drive again using System > Administration > Partition editor (gparted) or any partition manager

---

### Post by derrick81787 on 2008-07-31
> **forger said:**
> It will erase all your data on that hard drive
Choose the "one pass fill zeros" method.


If you're just trying to fill the entire hard drive with binary zeros (which it sounds like you're doing) you can just use the built-in Linux command "dd".  If the drive is not the same drive that you have the operating system on (which I believe yours is different) you don't even have to run it from a live CD.  You can just unmount every partition on the drive and then run the command below. [COLOR="Red"]MAKE SURE YOU REPLACE /dev/hdb WITH THE CORRECT DEVICE FOR YOUR PARTICULAR DISK![/COLOR] This will destroy all data on the disk. The block size can be just about any power of 2, but the larger the block size, the less time it will take (it does fewer writes to the disk because it writes more data per write).

```
sudo dd if=/dev/zero of=/dev/hdb bs=1M
```

forger's way sounds like it will work just fine (although I don't know the program), but I thought it would be cool to show you the built-in Linux way of doing things like that.

- Derrick

---

### Post by forger on 2008-08-01
> **derrick81787 said:**
> 
```
sudo dd if=/dev/zero of=/dev/hdb bs=1M
```


derrick, thanks about the block size tip, I didn't know you can improve speed with it :) does it have any limitations, what's the maximum block size I could use with dd command?

---

### Post by derrick81787 on 2008-08-01
> **forger said:**
> derrick, thanks about the block size tip, I didn't know you can improve speed with it :) does it have any limitations, what's the maximum block size I could use with dd command?

Well, if dd encounters an error, I think it's default behavior is to just skip the rest of that block and go on to the next one.  Therefore, larger block sizes will cause it to skip larger amounts of data in the event of data errors.

Also, cdroms have a certain sector size physically built in to the disk, so setting the block size in dd to the size of the sectors on the cdrom (or a multiple of the sector size) will cause it to read more efficiently.

Other than the behavior when dd encounters errors, I don't think there are any negative consequences of using larger block sizes.  I know the default is 512 bytes (which is typically the minimum that anyone uses). As far as I know, there isn't a maximum block size dd can handle, but you probably wouldn't want the block size to be bigger than the amount of data on the disk. I'm not a dd expert, though, so someone else would probably know more than I would.

- Derrick

---

