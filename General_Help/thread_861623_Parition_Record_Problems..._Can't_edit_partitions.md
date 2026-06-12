---
title: "Parition Record Problems... Can't edit partitions"
date: 2008-07-16
forum: General Help
---

### Post by thewhitenoise on 2008-07-16
I've been having this problem for a while now and I'm trying to get it fixed up. I'm kind of lost at this point so I'm not sure what to do next.

A few months ago, I decided to set up a windows partition on my 160gb HDD. I think at the time I had another partition there for backup, but moved that backup to another drive. I deleted the backup partition, created an NTFS partition (20gb), and resized my ubuntu partition to 123gb. I think somewhere in the Windows installation something went screwy because ever since I haven't been able to see those partitions in GParted (not even the live CD, which seems to be even more fantastic and powerful). Gparted always just showed the whole drive as unallocated with the DiskLabelType as unrecognized. 

At the time I think I read that the only way to fix that was to reset the Disk Label (which would erase the drive). Seeing as I didn't have another drive with enough free space to back up all the information, I just let it go. I've been using it fine since, all my information is there, I can access both partitions, they all mount fine, and I even upgraded to Hardy with no problems.

Fast forward to last nite.. I picked up another 160gb HDD so I could get this mess straightened out. The new drive is the exact same size (even the same model number), so I just did a clone of that drive to the new one using g4u thinking that it would fix it if it was indeed a Disk Label problem. About 20 hours later, I booted it up to see that the drive I cloned it to is in exactly the same position.. nothing on GParted, showing an unrecognized DiskLabelType, but all the information is there (I just can't boot it.. something about the MBR).

What's really weird is that when I type fdisk -l, nothing shows up. I just get a new line on my command prompt. There's no error at all, just blank.

```
$ fdisk -l
$ 

```

Here's what I get when I sudo gparted..

```
======================
libparted : 1.7.1
======================
Unable to open /dev/scd0 read-write (Read-only file system).  /dev/scd0 has been opened read-only.
Unable to open /dev/scd0 read-write (Read-only file system).  /dev/scd0 has been opened read-only.
Unable to open /dev/scd0 - unrecognised disk label.
Can't have overlapping partitions.
Can't have overlapping partitions.

```


Does anyone know where I should go from here? I've searched around the forums and couldn't find any information on it other than to just reinstall and start over. 

Is there a way to fix this drive the way it is without having to reinstall? Or is that the best option? Like I said, I have an identical clone of that drive, so all my information should be backed up. If I were to repartition the drive, is there an easy/efficient way of copying all of that information over from the backup to the newly-installed drive so that all my information/programs and configurations are the same?

On a side note.. since I have two drives of identical size, would it be feasible to set them up as a raid? They're both IDE drives.


UPDATE:

Tried fdisk -lu to see if I could get some information and this is what it's showing..

```
$ sudo fdisk -lu
omitting empty partition (5)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4b36bdea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    42106364    21053151    7  HPFS/NTFS
/dev/sda2        42106365   305058284   131475960   83  Linux
/dev/sda3       305058285   312576704     3759210    5  Extended
/dev/sda4       308833623   312576704     1871541   82  Linux swap / Solaris
/dev/sda5       305058411   308833559     1887574+  82  Linux swap / Solaris
omitting empty partition (5)

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4b36bdea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    42106364    21053151    7  HPFS/NTFS
/dev/sdb2        42106365   305058284   131475960   83  Linux
/dev/sdb3       305058285   312576704     3759210    5  Extended
/dev/sdb4       308833623   312576704     1871541   82  Linux swap / Solaris
/dev/sdb5       305058411   308833559     1887574+  82  Linux swap / Solaris

```

---

### Post by VMC on 2008-07-16
According to your 'fdisk' info, you now have to 160gb hard drives with the exact same partitions.

So is the problem you can't install Windows on that "/dev/sda1" partition?

By the way you don't need that extra swap partition.

---

### Post by thewhitenoise on 2008-07-16
Yes, that's exactly what I've got. I thought there was something wrong with the drive itself so I installed another 160gb drive and cloned the old one to that one. Seems like there's a problem with the partitions and not the drive.

I have windows installed on the NTFS partition and it seems to be working fine. The problem is that I can't edit the partitions at all and no partition manager will recognize them. I'd like to get rid of that Windows partition, as well as the extra swap partition, but I can't.

I'm thinking I might just need to reformat one of those drives with the partitions set up properly, reinstall, and move all the information over to the new one. If there's a way to fix the partitions, then great. If not, I've got it backed up just in case.

---

