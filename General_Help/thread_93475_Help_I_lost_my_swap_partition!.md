---
title: "Help I lost my swap partition!"
date: 2005-11-22
forum: General Help
---

### Post by zmg3 on 2005-11-22
I installed swsusp and neede more swap space. So I deleted my swap partition (/hda5) and created a new one (/hda4) with more space on it. However, it turns out swsusp wants to use /hda5. It even asks for a swap partition header. Before deleting I noticed that there where two partitions for /hda5. One was logical and the other was the actual swap. For /hda4 there is only one. Is there a way to make swsusp happy and create a new swap that is named hda5. I am not sure if hda4 is correctly installed. How do you in general install a new swap partition? How do you tell linux to use it?

Thanks a lot.

---

### Post by Pablo_Escobar on 2005-11-22
1. Creating partitions and manipulating them - I'd recommend gparted (Gnome) or qtparted (KDE)
2. You tell the OS which partition to use by an entry in fstab.

In case of any problem type in what :
> fdisk -l spits out
and
> /etc/fstabcontents

---

### Post by zmg3 on 2005-11-22
fdisk -l
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3921    31495401    7  HPFS/NTFS
/dev/hda2            4228        4838     4907857+  83  Linux
/dev/hda4            3922        3997      610470   83  Linux

Hda4 doesn't say swap. 

However,

cat /proc/swaps outputs:
Filename                                Type            Size    Used    Priority
/dev/hda4                               partition       610460  11820   -1

I am sure that something is wrong because swsusp instructs to do fdisk -l |grep swap to find the swap partition. However there is no line with swap from my fdisk command. Basically all that happened is that I lost the logical part of the partition. My new swap partition is just a vanilla primary partition.

---

### Post by soulestream on 2005-11-22
you need to delete the partition and recreate it as a swap partition. 

then just use the swapon command


soule

---

### Post by rmjokers on 2005-11-22
You can do this without deleting the partition.  Just make sure it is unmounted (swapoff).  Then run fdisk and change the type of the partition from 83 to 82.  Hopefully it will be detected properly after this change.

---

