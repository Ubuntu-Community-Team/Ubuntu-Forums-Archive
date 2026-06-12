---
title: "to make two partitions (one windows-non bootable NTFS I guess) and another kubuntu bo"
date: 2009-09-30
forum: Installation &amp; Upgrades
---

### Post by lse123 on 2009-09-30
I buy now a 500GB notebook EXTERNAL HDD, Well my install even 10 Linux in 10 partitions and a program to choose from where to boot(external) ? Linux(KUBUNTU) partition may be NTFS ? 

May use Kubuntu CDROM to make two partitions (one windows-non bootable NTFS I guess) and another kubuntu bootable(what FS you recommend?) ? ALL this DONE from kubuntu cdrom bootable 9.04(note: external disk i have)?

where I may find table of new releases (eg kubuntu 9.10 when?)?

---

### Post by oldfred on 2009-09-30
Linux cannot be NTFS, that is windows. A non-bootable NTFS is fine for sharing with a windows install. Ubuntu is EXT3 or EXT4. EXT3 is the current standard for Ubuntu installs and EXT4 will be the standard for new installs of Karmic.

If you are thinking of multibooting you need to review these sites:
boot 145 systems, older but still relevant
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)
One way to choose what to boot:
[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_)

Karmic is due to be released the end of October.

---

### Post by lse123 on 2009-09-30
how many linuxs i may insert on a single 500gb laptop external-HDD, ALL BOOTABLE with choice to boot between all ?

---

### Post by lse123 on 2009-09-30
non-bootable NTFS partition for sharing with windows can be done from kubuntu 9.10 ?

---

### Post by ezsit on 2009-09-30
> non-bootable NTFS partition for sharing with windows can be done from kubuntu 9.10 ?

Not that I know of. I believe to format NTFS you must do so from Windows. Please correct me if I am mistaken.

---

### Post by ajgreeny on 2009-09-30
> I believe to format NTFS you must do so from Windows. Please correct me if I am mistaken. I think you must therefore be corrected.  You can make and format a partition to ntfs in ubuntu easily with gparted, though you need to have **ntfs -3g** and **ntfsprogs** installed to do it.

---

### Post by oldfred on 2009-09-30
Windows and I think Opensolaris must be on one of the primary partitions. Most linuxes can be on a logical partition in the extended partition. You can have 4 partitions one of which may be an extended partition. Within the extended you can have many but I have not heard of a definitive number as the link above had 145 systems on 2 drives.

All the partitioning should be done from gparted either separately or as part of an install of a system. You need to plan ahead on what you want if you are planning many systems.

---

### Post by lse123 on 2009-10-02
I mean from UBUNTU OR KUBUNTU BOOTABLE CDROM, Is it need to have ntfs -3g and ntfsprogs OR exist such in bootable cdrom ?

---

