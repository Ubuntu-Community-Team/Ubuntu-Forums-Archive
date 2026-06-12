---
title: "Jaunty Installation Step 4 of 7"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by aknight_sa on 2009-04-28
while installing from the live CD and when reaching step 4

the window which says "starting disk partitioner" or something like that appears then disappears and nothing happens..

i also tried to access the Gparted tool to see the partitions and nothing happens as well..

seems the live cd is not able to read disk partitions.. how can this be solved??


i have a Dell Vostro 1000 laptop with Windows XP

---

### Post by lovinglinux on 2009-04-28
I don't know if this is the best solution, but worked for me on a similar situation. I wasn't able to install. Always stalled on the partitioning step.

So, I created the ext3 partitions for Ubuntu from Windows using PartitionMagic, then just mounted them during step 4 of the installation. It went all the way.

---

### Post by aknight_sa on 2009-04-28
i will be trying that.. but the issue is that i did have a ext3 partition. as i had ubuntu hardy installed.. i then deleted the partition and made it free.. but still

---

### Post by lovinglinux on 2009-04-28
> **aknight_sa said:**
> i will be trying that.. but the issue is that i did have a ext3 partition. as i had ubuntu hardy installed.. i then deleted the partition and made it free.. but still

You have free space, not a partition. I guess Ubuntu is having issues to create a partition from free space. So try what I suggested if you can. Please remember it must be an ext3 or ext4 partition to work. If you format it from Windows as NTFS it won't help.

---

### Post by aknight_sa on 2009-04-28
here is a copy of my fdisk

> root@ubuntu:/cdrom# fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      176714       88326    6  FAT16
/dev/sda2   *      176715    41142464    20482875    7  HPFS/NTFS
/dev/sda3        41142465   234436544    96647040    f  W95 Ext'd (LBA)
/dev/sda5        41142528   196555274    77706373+   7  HPFS/NTFS


i will try what you asked me to do

---

### Post by aknight_sa on 2009-04-28
what i dont really understand is why wont the installer reach step 4...and give me a choice of what to do with the hard disk..

it just hands after 3

---

### Post by lovinglinux on 2009-04-28
> **aknight_sa said:**
> what i dont really understand is why wont the installer reach step 4...and give me a choice of what to do with the hard disk..

it just hands after 3

I don't know about you system,  but in my case there was a whole series of problems related to some motherboard hacks implemented by the manufacturer to get the Vista compatibility logo, which messed with Linux installations. I was desperate to install Ubuntu, so I imagined that if the partition step is failing, why not try to create the partition with the native file system first. I really don't know if this has any valid influence, but it worked for me after dozens of failed attempts.

I also noticed that the installation process stalled before the step 4 if I selected a different system language. Leaving English as default gave me better results.

---

### Post by aknight_sa on 2009-04-29
problem resoved... i just had to wait for almost an hour for it continue!!

---

### Post by lovinglinux on 2009-04-29
> **aknight_sa said:**
> problem resoved... i just had to wait for almost an hour for it continue!!

w00t! \\:D/ =D>

---

