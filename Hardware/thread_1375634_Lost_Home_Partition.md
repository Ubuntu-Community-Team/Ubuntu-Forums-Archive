---
title: "Lost Home Partition"
date: 2010-01-08
forum: Hardware
---

### Post by ScoobyDan on 2010-01-08
HELP!!! :shock:

I have been a 4-year user of Ubuntu, but for the last week or so I have been trying Mandriva on a spare partition. As I was only testing Mandriva, I had the root and home directories on the same partition, but my "normal" home partition is seperate, so last night I decided to re-install Mandriva, but this time to use the main partition as my home partition.

My partitions are as follows:

Ext 4 (Ubuntu root) 20GB
Ext 4 (Mandriva testing) 20GB
Ext 4 (Home) 460GB
Swap 2GB

The install went fine, and I installed all the updates needed. I was experiencing a few minor problems (newly installed fonts not rendering correctly in Firefox, for example), so I decided to reboot to see if that would cure it. On reboot I was confronted with a "Cannot enter home" error message, and I was unable to log in. I tried a live CD - and identified the problem - only the Ubuntu and Mandriva root partitions were available, the Home partition was marked as "Linux native" in the Partition Manager! :shock:

After searching the Mandriva forum, I found a recovery app called "testdisk", which I installed onto a Live system and ran against the drive. It located my Home partition, so I told it to re-write the partition table with that partition as Ext 4. All seemed to go well, but when I rebooted the PC hung at the "Grub..." text (not even loading the Grub boot loader).

I can now see the Home partition in a Live session Partition Manager, but it reports that the partition needs to be formated before it can be mounted. As I have over 400GB of data on that partition (without a recent backup) I don't want to do this!

Any ideas how to recover my partition, or should I resign myself to losing all that data? :cry:

Yours hopefully,

Daniel

fdisk -l output:

```
ffdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe611e611

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            2433        4864    19535040   83  Linux
/dev/sda3            4865       60801   449313952+   f  W95 Ext'd (LBA)
/dev/sda5            4865       60546   447265633+  83  Linux
/dev/sda6           60547       60801     2048256   82  Linux swap / Solaris
```

---

