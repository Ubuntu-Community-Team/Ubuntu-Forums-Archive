---
title: "sda or sdb?"
date: 2009-02-07
forum: Installation &amp; Upgrades
---

### Post by Fishhooker on 2009-02-07
I posted this over at the "Absolute Beginner Talk" forum, but I was getting no answers, and realized that this would be a better place to put my question.

I've got a Toshiba Satellite X205-SLi6, with two physical hard drives. I've been using Windows Vista ever since I got this computer; all of my data is on C:, and I plan to install Ubuntu Studio 8.10 on D:.

I go to the partitioning menu, and I select "Guided: Use Entire Disk," and that's when it all goes pear shaped. It shows me two options that I've never seen before:

SCSI3 (0,0,0) (sda)
SCSI5 (0,0,0) (sdb)

Which one of these translates to C:, and which translates to D: ?

---

### Post by Pumalite on 2009-02-07
Post:
```
sudo fdisk -lu
```

---

### Post by Fishhooker on 2009-02-07
Ah... There's just one problem with using that: I don't have any variant of Linux installed yet.

---

### Post by Ericyzfr1 on 2009-02-07
If you choose manual, it will then show you the partitions on every hard drive, if you remember the size of your vista partition you should be able to tell which hard drive is which.

---

### Post by cdtech on 2009-02-07
Normally the primary drive (your windows install) would be sda and your secondary would be sdb. You could power down and remove your windows drive (if at all possible) then do the install. This way your sure not to overwrite the Windows drive. Although your BIOS is most likely set up to boot from the primary drive of sda (Windows)........

---

### Post by 73ckn797 on 2009-02-07
> **Fishhooker said:**
> I posted this over at the "Absolute Beginner Talk" forum, but I was getting no answers, and realized that this would be a better place to put my question.

I've got a Toshiba Satellite X205-SLi6, with two physical hard drives. I've been using Windows Vista ever since I got this computer; all of my data is on C:, and I plan to install Ubuntu Studio 8.10 on D:.

I go to the partitioning menu, and I select "Guided: Use Entire Disk," and that's when it all goes pear shaped. It shows me two options that I've never seen before:

SCSI3 (0,0,0) (sda)
SCSI5 (0,0,0) (sdb)

Which one of these translates to C:, and which translates to D: ?

sda wil generally be what Windows calls "C" and sdb would be the "D" drive. Linix does not use that designation.

Look at it this way:

C = sda = hd0
D = sdb = hd1

and so forth. sda is the Linux designation. hd0 is how grub lists drives. Each subsequent drive will incremnt up either "sda, sdb, sdc" or "hd0, hd1, hd2".

---

### Post by Fishhooker on 2009-02-07
Thanks guys!

I'm also wondering, what does this:

> **Pumalite said:**
> Post:
```
sudo fdisk -lu
```

do?

I'm downloading vanilla Ubuntu in order to make a live CD so that I can do that terminal command, but what exactly would it tell me if I did that?

---

### Post by perlluver on 2009-02-07
> **Fishhooker said:**
> Thanks guys!

I'm also wondering, what does this:



do?

I'm downloading vanilla Ubuntu in order to make a live CD so that I can do that terminal command, but what exactly would it tell me if I did that?

It will tell you what each hard drive contains, and the filesystem type.  For example, if Windows is installed, it will be NTFS.

---

### Post by Shazaam on 2009-02-07
A sample output of that terminal code...
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00047d37

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   625137344   312568641    5  Extended
/dev/sda5             126     4369679     2184777   82  Linux swap / Solaris
/dev/sda6         4369743    53817749    24724003+  83  Linux
/dev/sda7        53817813   136086614    41134401   83  Linux
/dev/sda8       136086678   261088379    62500851   83  Linux
/dev/sda9   *    261088443   469322909   104117233+  83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000096f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   156296384    78148161    7  HPFS/NTFS

```

---

### Post by Fishhooker on 2009-02-07
So for that sample output, one would infer that you have Linux installed on sda, and Windows installed on sdb?

EDIT: I went into the live CD, did sudo fdisk -lu, and this is what it said. 

```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd405d405

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3074047     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *     3074048   390721535   193823744    7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5d379805

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   390721535   195359744    f  W95 Ext'd (LBA)
/dev/sdb5            4096   390721535   195358720    7  HPFS/NTFS

```

I have no idea how to decipher what the terminal says (other than the filesystems). All I know is that the drive with more free space is the one I should be doing the installation on.

---

### Post by Shazaam on 2009-02-09
```
"So for that sample output, one would infer that you have Linux installed
on sda, and Windows installed on sdb?"
```

Yes they are. Originally I had XP and a few flavors of linux on the 80 gig IDE drive. Then I bought the 320 SATA drive for more room. I eventually got tired of Windows bothering linux so I put it on the IDE drive by itself and have used the 320 exclusivly for linux. The fun part was getting XP configured as not being the primary os. There are threads here on the forums on how to do this. Normally you would need to have Windows first on the boot drive and then the other operating systems next.

```
"I have no idea how to decipher what the terminal says (other than the filesystems).
All I know is that the drive with more free space is the one I should be doing
the installation on."
```

You can use gparted on the livecd to figure which one has the most free space (System>Administration>Partition Editor). If you go to the upper right you will see a drop down box that says "sda"; click it to get to sdb.

---

### Post by Pumalite on 2009-02-09
If you are going to install Ubuntu in a different drive than Windows; read this:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)
Did you format that drive?
Use TestDisk to check your drive;
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

