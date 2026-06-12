---
title: "Partitioner not detecting partitions on HDD"
date: 2009-09-27
forum: Installation &amp; Upgrades
---

### Post by boolean22222 on 2009-09-27
Trying to install 9.04 on an XPS M1530 (Dell) with an unallocated block of ~20G.  The disk has been verified and I have tried pre-formatting the unallocated space to an 18G ext3 and 2G swap and that doesn't help either.

Here is the layout:

```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3ad50b5e

Device       Boot     Start            End            Blocks          Id    System
/dev/sda1              63                64259         32098+        de    Dell Utility
/dev/sda3   *         53616640     385476607   165929984   7      HPFS/NTFS
/dev/sda4              64260          390719487   195327614   5      Extended
Partition 4 does not end on cylinder boundary.
/dev/sda5              64328          12659219     6297446      7      HPFS/NTFS
/dev/sda6              385478656   390719487   2620416      dd    Unknown
```

sda1=dell jazz
sda3=vista
sda4=unallocated space
sda5=vista
sda6=media direct

Any thoughts on getting ubuntu running on here?
--

Just moved the unallocated space out of the extended partition.  Still no luck.
Image from Win: [IMG]http://i38.tinypic.com/v8pu9s.jpg[/IMG]

---

### Post by louieb on 2009-09-27
Its that primary partition sda3 is inside extended partition sda4 - non-standard partitioning -  Gparted and the Ubuntu installer sees that and treats the disk as if it does not have any partitions at all. 

You might be able to use the manual partition option on the alternated CD. to create logical partitions for Ubuntu.  from the fdisk output you have free space between sda5 and sda3.

```

Device       Boot     Start            End            Blocks          Id    System
/dev/sda1              63              64259         32098+        de    Dell Utility
/dev/sda4              [COLOR=Red]64260       390719487[/COLOR]   195327614   5      Extended
/dev/sda5              64328        12659219     6297446   7      HPFS/NTFS
/dev/sda3   *         [COLOR=Red]53616640     385476607 [/COLOR]  165929984   7      HPFS/NTFS
/dev/sda6             385478656    390719487   2620416      dd    Unknown
Partition 4 does not end on cylinder boundary.

```

---

### Post by boolean22222 on 2009-10-03
I moved the unpartitioned space outside of the other so that the partitioner would not get confused.  Unfortunately, it still is not detecting anything.  Here is the setup:

```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3ad50b5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       64259       32098+  de  Dell Utility
/dev/sda3   *    53616640   385476607   165929984    7  HPFS/NTFS
/dev/sda4        41013945   390719487   174852771+   5  Extended
Partition 4 does not end on cylinder boundary.
/dev/sda5        41014008    53608904     6297448+   7  HPFS/NTFS
/dev/sda6       385478656   390719487     2620416   dd  Unknown
```

Thoughts?

---

### Post by louieb on 2009-10-03
Its not the unallocated space thats confusing it. Its the fact that primary partition sda3 is inside extended partition sda4.  

[Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm")

---

### Post by boolean22222 on 2009-10-24
I am not sure I understand why it is a problem.  If I am trying to install to the unallocated space which is outside of the extended, what is the issue?  Is there anything I can do to fix it w/o re-installing and making sure that no ext. partitions are created?

Thanks  :guitar:

---

