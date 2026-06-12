---
title: "SiI 4726 Port Multiplier Config &amp; Partition Help"
date: 2010-07-05
forum: Hardware
---

### Post by SeekerU on 2010-07-05
I am seeking assistance hacking together a eSATA storage solution for an older PC that has a current Lucid server install.

I have a nice, but older PC that needed some additional storage.  Rather than continuing to stuff the box with IDE or expensive SCSI drives, I went looking for an eSATA RAID storage enclosure solution.  I'm 75% of the way to having a working solution.  However, I'm currently dead-ended looking for a way to configure the RAID and partition my array.  Does anyone have any suggestions for making this work?

Here is what I have:

PCI to eSATA HBA: Koutech 4 x Hi-Speed USB 2.0 + 2 x SATA
<http://www.newegg.com/Product/Product.aspx?Item=N82E16815201016>

SiI 4726 Based Storage Enclosure: AMS VENUS ES5 DS-315SES
<http://www.newegg.com/Product/Product.aspx?Item=N82E16817332021>

Drives: a pair of Seagate Barracuda ST31500341AS
<http://www.amazon.com/gp/product/B00066IJPQ/ref=oss_product>

The HBA was installed and recognized by the PC BIOS.  The HBA recognizes the drive enclosure with the drives.

  lspci
  -----------------
  00:13.3 Mass storage controller: Silicon Image, Inc. SiI 3512 [SATALink/SATARaid] Serial ATA Controller (rev 01)
  00:13.3 0180: 1095:3512 (rev 01)
        Subsystem: 1095:3512
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 3
        I/O ports at eca8 [size=8]
        I/O ports at ecb8 [size=4]
        I/O ports at ecb0 [size=8]
        I/O ports at ecbc [size=4]
        I/O ports at ecc0 [size=16]
        Memory at fedfb400 (32-bit, non-prefetchable) [size=512]
        [virtual] Expansion ROM at 08000000 [disabled] [size=512K]
        Capabilities: <access denied>
        Kernel driver in use: sata_sil
        Kernel modules: sata_sil


  fdisk -l
  -------------------
  Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
  255 heads, 63 sectors/track, 182401 cylinders
  Units = cylinders of 16065 * 512 = 8225280 bytes
  Sector size (logical/physical): 512 bytes / 512 bytes
  I/O size (minimum/optimal): 512 bytes / 512 bytes
  Disk identifier: 0x00000000

  Disk /dev/sdc doesn't contain a valid partition table

Out on the Silicon Image website, there was a SiI4726 Manager for Linux that is intended to configure and partition
  <http://www.siliconimage.com/support/searchresults.aspx?pid=74&cat=24>
After a number of challenges, I've been able to get this software to execute.  However, this software does not see the drives and I am out of tricks.  This is where I am looking for help.

When using this SteelVine Manager Software, looking in the software log, it says that it sees devices 0/, 1/, 2/ and 26/ and it doesn't recognize any of them as an SiI 4726.

Some of the challenges...
- This software is dependent upon libstdc++5; last supported on Jaunty.  I was able to install the package on Lucid and, for this purpose, it appears to be working.
- This software is also dependent upon an X server environment.  I really didn't want to install a GUI environment on this already burdened system.  I've installed the basic X Server environment with Openbox window manager.  This appears to be sufficient.

---

### Post by iaw4 on 2010-08-15
did this work?  I am thinking of getting something similar.

/iaw4

---

### Post by SeekerU on 2010-08-18
Unfortunately, no.  I was not able to get the SteelVines code to run on Ubuntu.  I ended up hooking the storage unit up to a Windows platform to configure the RAID and partition it.  I then returned it to my Ubuntu platform and I was able to mount and format the array.  Unfortunately, Ubuntu doesn't recognize that I (as root) have write authority to the now formatted array and I haven't had time to pursue it further.

---

