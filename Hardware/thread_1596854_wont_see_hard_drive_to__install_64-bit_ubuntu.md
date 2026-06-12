---
title: "wont see hard drive to  install 64-bit ubuntu"
date: 2010-10-14
forum: Hardware
---

### Post by burnza1 on 2010-10-14
I tried 10.04 and 10.10 to install onto a wiped clean hard drive that it wont see the hard drive to install I'm trying to install onto my Western Digital Caviar Black 1TB SATA3 drive, it boots off the cd fine and detects everything except my hard drive. Any ideas?

---

### Post by coffeecat on 2010-10-14
Is this an "advanced format" drive? I've no practical experience of them but I know they're causing problems. Have a look at this article:

[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html)

When you say it won't see the drive, is that in the installer? In the live CD session, go to System > Adminstration > Gparted. Does that see it? The linked article has some advice on using Gparted. If you can, you could set up your partitions manually before starting the installer.

---

### Post by burnza1 on 2010-10-14
it doesnt see it in the installer or gparted in the live cd

---

### Post by srs5694 on 2010-10-14
This is not an Advanced Format issue; the problem with Advanced Format drives is that if partitions are misaligned, performance suffers. There's no problem detecting such drives, provided the rest of the hardware and software chain (cables, disk controller, drivers, etc.) is working.

There are several possible causes of failures to detect hardware. Some things you can try include:


[list]
[*]Try fiddling with AHCI options in the BIOS.
[*]Try unplugging the disk cable from the motherboard and plug it back into another SATA socket. Repeat until you've tested all the SATA sockets on the motherboard or until the disk starts working.
[*]Try replacing the SATA cable.
[*]Try another Linux distribution or an emergency disc like [PartedMagic](http://partedmagic.com) or [System Rescue CD.](http://www.sysresccd.org/Main_Page) The goal isn't to install Ubuntu this way, just to see if other Linux distributions can see the disk. If not, then it's likely a hardware fault or completely unsupported hardware; but if you can see the disk, there may be a workaround in Ubuntu.
[*]In an Ubuntu live CD, type "dmesg | less" and scan for messages relating to the hard disk, including anything about SATA or SCSI. There may be clues here. Post anything suspicious here if you need help interpreting it.
[*]In an Ubuntu live CD, type "lspci" and post the lines relating to the disk controller (probably labelled as SATA or IDE). You could also try Googling the disk controller model along with "Linux."
[/list]

---

### Post by Yellow Pasque on 2010-10-14
So, does the BIOS detect the disk?

---

### Post by garvinrick4 on 2010-10-14
```
I have seen it as simple as removing this before install on CD or
USB. "Worth the try only takes a second to do" Worked in a lot of cases of know drive visable at install.
[CODE]sudo apt-get remove dmraid
```


rick@rick-laptop:~$ aptitude show dmraid
Package: dmraid                          
State: not installed
Version: 1.0.0.rc16-3ubuntu2
Priority: optional
Section: admin
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 188k
Depends: libc6 (>= 2.4), libdmraid1.0.0.rc16 (>= 1.0.0.rc16), libselinux1 (>=
         1.32), libsepol1 (>= 1.14), udev, dmsetup
Description: Device-Mapper Software RAID support tool
 dmraid discovers, activates, deactivates and displays properties of software
 RAID sets (eg, ATARAID) and contained DOS partitions. 
 
 dmraid uses the Linux device-mapper to create devices with respective mappings
 for the ATARAID sets discovered. 
 
 The following formats are supported: 
 Highpoint HPT37X/HPT45X
 Intel Software RAID
 LSI Logic MegaRAID
 NVidia NForce RAID (nvraid)
 Promise FastTrack
 Silicon Image(tm) Medley(tm)
 VIA Software RAID
 
 Please read the documentation in /usr/share/doc/dmraid BEFORE attempting any
 use of this software. Improper use can cause data loss!
Homepage: [http://people.redhat.com/~heinzm/sw/dmraid/](http://people.redhat.com/~heinzm/sw/dmraid/)

rick@rick-laptop:~$ 
[/CODE]

---

### Post by cascade9 on 2010-10-14
It not an advanced format issue, srs5694 is 100% correct. 

> **burnza1 said:**
> I tried 10.04 and 10.10 to install onto a wiped clean hard drive that it wont see the hard drive to install I'm trying to install onto my Western Digital Caviar Black 1TB SATA3 drive, it boots off the cd fine and detects everything except my hard drive. Any ideas?

Wiped? Is that a newly installed drive in your system, or something you've been running for a while?

If its newly installed, are you running it on a SATA RAID port? Quite a few motherboards that only have SATA2 support from the main chipset have add-on RAID chips thatdo SATA3. Sems liek the right idea to run  a SATA3 drive on the SATA3 port, right? But a lot of those SATA chips have horrible linux support. 

 There is also the chance that your running the drive on an older chipset with SATA1 support, in which case you might need to...gasp!....play with the jumpers on the drive to limit it.

> **Temüjin said:**
> So, does the BIOS detect the disk?

If the BIOS doesnt see the drive, you'll never get the drive to be seen by any OS. ;)

---

### Post by burnza1 on 2010-10-14
bios detects it it works in windows 7 just linux wont see the disk, i tryed others like fandora but the same thing.

---

### Post by cascade9 on 2010-10-14
That sure sound like what happens if you try to use a SATA3 expansion chip with bad, or 0, linux support.

---

### Post by burnza1 on 2010-10-20
> **cascade9 said:**
> That sure sound like what happens if you try to use a SATA3 expansion chip with bad, or 0, linux support.
  
i guess im sticking with windows :(

---

### Post by Yellow Pasque on 2010-10-20
> **burnza1 said:**
> i guess im sticking with windows :(
Or you could jumper the drive to force SATA2 if that's the issue.  [http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=5387&p_created=&p_cats=185&p_cv=1.185&p_pv=2.279&p_prods=227%2C279#jumper](http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=5387&p_created=&p_cats=185&p_cv=1.185&p_pv=2.279&p_prods=227%2C279#jumper)

---

### Post by cascade9 on 2010-10-20
> **burnza1 said:**
> i guess im sticking with windows :sad:

What motherboard are you using? 

It should be a fixable problem, you will probably just have to move the drive to a different SATA port. 

> **Temüjin said:**
> Or you could jumper the drive to force SATA2 if that's the issue.  [http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=5387&p_created=&p_cats=185&p_cv=1.185&p_pv=2.279&p_prods=227%2C279#jumper](http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=5387&p_created=&p_cats=185&p_cv=1.185&p_pv=2.279&p_prods=227%2C279#jumper)

Could be that as well, but I think its more likely that its a crummy SATA port.

---

### Post by royleith on 2010-12-13
Hi srs5694,

Just to let you know that it is not just high-end stuff causing the problem. i swapped out a fine, working 80GB slave for a brand new IDE WD Caviar Green 160GB which would otherwise have gone to waste. The BIOS finds it, Windows 98 finds it (don't ask!), but Kubuntu 10.10 does not and neither does the System Rescue CD. I partitioned it up with a Swap and a Fat32 using Partition Magic (hey, I was desparate!), but Linux just won't look at it. 

I tried your dmesg command and got the following,
> 
[    1.855306] ata1.00: ATA-7: ST3250620A, 3.AAE, max UDMA/100
[    1.855312] ata1.00: 488397168 sectors, multi 16: LBA48 
[    1.869920] ata1.01: ATA-8: WDC WD1600AAJB-00J3A0, 01.03E01, max UDMA/133
[    1.869926] ata1.01: 312581808 sectors, multi 16: LBA48 
[    1.930298] ata1.00: configured for UDMA/100
[    1.954733] ata1.01: failed to IDENTIFY (I/O error, err_mask=0x2)
[    1.954738] ata1.01: revalidation failed (errno=-5)
[    7.063763] ata1.00: configured for UDMA/100
[    7.086727] ata1.01: failed to IDENTIFY (I/O error, err_mask=0x2)
[    7.086732] ata1.01: revalidation failed (errno=-5)
[    7.086739] ata1.01: limiting speed to UDMA/100:PIO3
[   12.213915] ata1.00: configured for UDMA/100
[   12.238738] ata1.01: failed to IDENTIFY (I/O error, err_mask=0x2)
[   12.238743] ata1.01: revalidation failed (errno=-5)
[   12.238748] ata1.01: disabled
[   12.238769] ata1.00: failed to set xfermode (err_mask=0x40)
[   17.364076] ata1.00: configured for UDMA/100
[   17.364337] scsi 0:0:0:0: Direct-Access     ATA      ST3250620A       3.AA PQ: 0 ANSI: 5
[   17.364705] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   17.365365] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[   17.365469] sd 0:0:0:0: [sda] Write Protect is off
[   17.365476] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   17.365520] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   17.365842]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 sda8 sda9 >


Which I interpret as 'this CPU's clock cycles are too far apart for it to live'. The report was similarly scathing about DMA on the two optical drives.

Is there no hope? Should I just revert to the old slave drive and try to find a newer motherboard to run the new drive. The lack of DMA all round would explain the snail like performance of this venerable Athlon system.

Regards
Roy Leith

---

