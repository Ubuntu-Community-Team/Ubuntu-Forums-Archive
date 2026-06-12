---
title: "How to check if a SATA port has died or HDD is dying (from the command line)?"
date: 2011-04-16
forum: Hardware
---

### Post by pedrogent on 2011-04-16
I recently got a bit of a shock as one of my HDDs seemingly died on me. NB: I've posted something similar [here]("http://askubuntu.com/questions/34862/weak-filesystem-seems-to-have-died-what-can-i-do") but have yet to get the answer I seek, although someone told me to put my HDD in the freezer!

Initially the problem was like this: I returned from a holiday to find my Ubuntu 'server' not functioning as it should. Specifically, one disk seemed to have died. I have Ubuntu 10.10 set-up as a 'server/NAS'. (I've installed netatalk and avahi-daemon to facilitate AFP shares.) There are two physical disks. The 'data' disk was the one that's wasn't working. This disk is formatted using the GUID partition table. It's the first time I've done this in a Linux environment, usually choosing an msdos partition map.

During POST, the disk in question was not found. I use AHCI mode.

The relevant bits from my /etc/fstab look like this:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=dd096328-2e0d-46d1-a630-760f895ece15 /                     ext4 errors=remount-ro,user_xattr 0       1
UUID=4d901313-a4f7-45b3-b15a-a70b2a4182e2 /media/data           ext4    defaults                  0       2
UUID=69a1dd0a-9da2-4ca4-bd21-00cd5d23ee0d none                  swap    sw                        0       0
```

If I ran sudo blkid '/dev/sdb1' (i.e. /media/data) wasn't showing up. Prior to this there were reports of a 'weak filesystem' during reboots, and e2fsck suggested I move the superblock on the drive.

I solved the problem by plugging the HDD into another SATA port. This leads me to believe the first SATA port is faulty. If so, I should replace the motherboard. But perhaps the HDD itself is faulty, or perhaps I've done the GUID partition incorrectly.

Is there a way to determine the health of that SATA port & HDD from the command line?

Thanks in advance.

---

### Post by Yellow Pasque on 2011-04-16
The easiest way is to try another SATA device on that port. Out of curiosity, what mobo and HD are you using?

---

### Post by pedrogent on 2011-04-16
The motherboard is an [Asus P7P55D-E]("http://www.asus.com/Motherboards/Intel_Socket_1156/P7P55DE/").

The HDD is a [WD6402AAEX-00Z3A0]("http://wdc.com/global/products/specs/?driveID=855&language=1").

Disk Utility reports that the drive is fine for what it's worth. This is in the new SATA port. I'm worried that plugging it back into the port I think is defective may cause data corruption. Should I be?

---

### Post by varunendra on 2011-04-16
As for testing the physical status of HDD, you've already done what I could suggest : > **pedrogent said:**
> ....I solved the problem by plugging the HDD into another SATA port.

As for testing the port, +1 to Temüjin : > **Temüjin said:**
> The easiest way is to try another SATA device on that port. 


Now for your last question :
> **pedrogent said:**
> The motherboard is an [Asus P7P55D-E]("http://www.asus.com/Motherboards/Intel_Socket_1156/P7P55DE/").

The HDD is a [WD6402AAEX-00Z3A0]("http://wdc.com/global/products/specs/?driveID=855&language=1").I'm worried that plugging it back into the port I think is defective may cause data corruption. Should I be?

yes, you should, if the port is really unstable and gets disconnected again while a write operation is in progress. Try using that port for your optical drive if you have one.

Your mobo & Hdd both are good brands and models, so it seems unlikely (although not impossible!) that any of them could get defective without tampering (you said it already 'died' when you returned from holiday). I've seen the "drive not detected" type problem very often caused due to using cheap sata cable. So if you are not already using the original sata cable provided with the motherboard, try replacing it with a good one, or preferably - the original one.

Also, the disk configuration does not seem to be a reason since it was absent during POST also, and AHCI is a common mode to use.

---

### Post by Yellow Pasque on 2011-04-16
I see your disk is SATA 6.0Gb/s. Are you using the gray SATA ports attached to the Marvell controller, the black one to the JMicron, or the light blue ones attached to the ICH SB?

Only the Marvell ports are SATA 6.0Gb/s. SATA 6.0Gb/s doesn't really help mechanical drives, but I could see a possible issue when hooking to a SATA 3.0Gb/s port,  although this shouldn't be an issue nowadays. Nevertheless, WD provides a jumper to force 3.0Gb/s mode: [http://wdc.custhelp.com/app/answers/detail/a_id/5387#jumper](http://wdc.custhelp.com/app/answers/detail/a_id/5387#jumper)

---

### Post by pedrogent on 2011-04-16
@varunendra: The SATA cable is the original one. Unfortunately my only optical drive is a USB device.

@Temüjin: I'm using the light blue Intel SATA ports. Thanks for that link. I had no idea there were backwards compatibility issues here. Jumpers! Wow - I thought I left jumper world years ago. I guess I'll take a look at that tomorrow. I've no problems with using the Intel ports as I realize I'll see no benefit from next-gen SATA ports. I just bought this HDD because it was the cheapest available.

***

To both of you, you've been very helpful. Unfortunately I've got to call it a night now because my head is spinning and I'm slightly worried that I'm about to lose all my valuable data (my back-up external drive is also playing up... but that's a whole different story.)

---

### Post by pedrogent on 2011-04-27
A bit more on this. I have three SATA controllers at my disposal:

```
$ lspci | grep SATA
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
03:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
04:00.0 SATA controller: Marvell Technology Group Ltd. 88SE9123 PCIe SATA 6.0 Gb/s controller (rev 10)
```

I switched the drive from SATA2 to SATA3 and I got about a week of use before failure again. Not found during POST and nowhere to be seen in the BIOS screens.

So I switched to the JMicron controller. This didn't help. It's still not detected during POST.

I will RMA the drive tomorrow but I wonder if there is anything at all I can do to get this drive back online as a last resort. I have an idea about changing the location of the superblock but I'm unsure how I'd go about doing this (and if it would do anything useful anyway).

---

### Post by pedrogent on 2011-04-27
On the advice of a member over at superuser.com I changed the SATA cable and now everything is as it should be.

Very relieved.

:)

---

