---
title: "[SOLVED] SATA HD not found"
date: 2008-03-13
forum: Hardware &amp; Laptops
---

### Post by Kimos on 2008-03-13
I'm running 7.10 off an IDE drive, and I've just picked up my first SATA drive to add on as extra storage. I plugged in the drive and it powers up, but I'm not able to spot it. It doesn't show up in fdisk or even in what the BIOS spits out on startup.

It's a Western Digital 320GB SATA II drive. My motherboard is an ASUS K8V-X SE. The manual for my motherboard only has one SATA related option "OnChip SATA Boot ROM [Enabled][Disabled]" and I get no results on either setting. Though, the manual does expressly state SATA1 and SATA2 compatibility.

Here's my output from fdisk. All there is is my IDE drive and my USB external backup drive.

```

$ sudo fdisk -l

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x223fcbe3

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2550    20482843+   c  W95 FAT32 (LBA)
/dev/hda2            5111       30401   203149957+   7  HPFS/NTFS
/dev/hda3            2551        4998    19663560   83  Linux
/dev/hda4            4999        5110      899640    5  Extended
/dev/hda5            4999        5110      899608+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    c  W95 FAT32 (LBA)

```

Anyone have suggestions or some experience to share?

---

### Post by pbpersson on 2008-03-13
Make sure you have the drive plugged into the SATA1 and not the SATA2 port on the motherboard

Make sure you have the drive jumpered for the 150 speed and not the 300

Did you use an adapter to convert the standard power plug to the SATA style or do you have a special SATA power feed from the power supply?

---

### Post by egalvan on 2008-03-13
> **Kimos said:**
> I'm running 7.10 off an IDE drive, and I've just picked up my first SATA drive to add on as extra storage. I plugged in the drive and it powers up, but I'm not able to spot it. It doesn't show up in fdisk or even in what the BIOS spits out on startup.

It's a WD 320GB SATA II. My motherboard is an ASUS K8V-X SE. ..manual .. only has one SATA related option "OnChip SATA Boot ROM [Enabled][Disabled]" and I get no results on either setting. Though, the manual does expressly state SATA1 and SATA2 compatibility.


Anyone have suggestions or some experience to share?

OK, from my "experience" files:

First off, hit ASUS's web-site for a BIOS update on your board. (this assumes a retail mobo... if not, then check the OEM's web-site);

then hit WD's web-site for the diagnostic software. You may have gotten it with your drive if it was RETAIL, OEM's tend to not send the CD. Run it and see what happens.

Second, check CAREFULLY (tedious, I know) through ALL the BIOS screens for a setting that may enable/disable the ON-BOARD SATA. and any COMPATIBILITY MODE. I have seen this many times. The manual may not have ALL the info.

Third, the SATA cable. drive or mobo itself may be bad. :(   Check BOTH CABLE AND DRIVE on another KNOWN-WORKING system, or check with a KNOWN-WORKING cable and drive on yours. This can be difficult to achieve. Geek-type friends can be helpful, or a computer club, or a friendly repair place may do it for you. Taking just the cable and drive and asking "what will you charge me to see if this works?" will usually get you the "just take a minute, no charge" answer, and the small local shops are a better bet than BestBuy (unless you bought the drive there).

And last, SATA1   SATA2  tend to be the channel numbers, or "drive #1"  "drive #2".. 
and   SATA-I  SATA-II tend to be generation... "first"  "second"
SATA-II is usually back-wards compatible with SATA-I. Your mobo model number sound as if it pre-dates SATA-II. This is not always a problem... I run a SATA-II on SATA-I mobos.



Let us know of any progress, or lack of.
:popcorn:

---

### Post by Kimos on 2008-03-13
Thank you both of you for your suggestions.

Cruised around the BIOS again but there was nothing else. Already had it in SATA1, but wasn't sure if my older board would support SATA II. Quite frankly, I was surprised it had SATA at all. 

I ended up on the WD website and found that the compatibility mode for different speeds was buggy. I put a jumper on pins 5 and 6 to speed it down. Rebooted and all is well.

```

$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

...
```

Cheers!

---

