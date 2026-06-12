---
title: "GParted shows entire drive unallocated but fdisk doesn't"
date: 2009-02-08
forum: Hardware
---

### Post by FrancoFerrucci on 2009-02-08
Hi people,

I have Windows XP and Ubuntu 8.10 installed in my 320GB HD. I tried to modify the sizes of the partition using Partition Magic (big mistake?) and I don't know why something went wrong. I still CAN access normally the two OS with the grub but, using GParted under Ubuntu, it says that the entire disk is unallocated. I know something is wrong in the partition table but I don't know how to solve it without losing the two OS. 
The sudo fdisk -l and -lu outputs are:


```
sudo fdisk -l
[sudo] password for franco: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x1f731f72

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       27087   204777688+   7  HPFS/NTFS
/dev/sda2           27087       41345   107795677+   5  Extended
/dev/sda5           27087       40760   103370211   83  Linux
/dev/sda6           40760       41346     4425876   82  Linux swap / Solaris
franco:/$ sudo fdisk -lu

Disk /dev/sda: 320.0 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1f731f72

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   409555439   204777688+   7  HPFS/NTFS
/dev/sda2       409545045   625136399   107795677+   5  Extended
/dev/sda5       409545108   616285529   103370211   83  Linux
/dev/sda6       616285593   625137344     4425876   82  Linux swap / Solaris

```

Apparently there are some overlappings! Do you know how to fix it without damaging the two OS?

Thanks in advance
Franco Ferrucci

---

### Post by slavik on 2009-02-08
is /dev/sda the whole drive and can you show us a screenshot of what gparted shows?

---

### Post by FrancoFerrucci on 2009-02-08
Hi, 

Yes /dev/sda is the whole drive. I have attached a snapshot of GParted.


I forgot to say that after exiting Gparted this text appears in the terminal:


======================
libparted : 1.8.9
======================
Can't have overlapping partitions.



Thanks

Franco

---

### Post by slavik on 2009-02-08
I think you will have to use partition magic in order to under the operations you did.
there is also another utility (testdrive?) but I am not sure if it can help you.

if you have more than 320GB of free space elsewhere, you can even backup your entire drive using dd :)

---

### Post by FrancoFerrucci on 2009-02-08
Everything is fixed now!!! Thanks to TESTDISK!!! This wonderful program solved the problem of the overlapping partitions without spoiling the two OS installed!!

Thanks slavik!!!

---

