---
title: "NTFS partition not recognisable."
date: 2010-10-19
forum: Hardware
---

### Post by AsgerJorn on 2010-10-19
An error has occured as I used the partition-manager in Windows XP.
Now the ubuntu partition is not recognised during boot. I get a 'grub error: no such partition'

I accessed the Live-CD installation, also the text installer, the 'rescue system' option and OEM installer, but these does not recognise the NTFS drive as a partition.

When I boot Kubuntu 10.10 from live cd the NTFS drive is mounted and recognized (I have also managed files on the drive - it is fully functional), but as said, it is impossible to manage as a partition and therefore boot in windows.

I wish to be able to acces my original Windows XP partition, since I have some useful settings and the office pack that I do not wish to loose.

Is that possible?

I have attached the boot script result file.

EDIT: I am now running Kubuntu 10.10 from Live CD, as the only way to boot, because Kubuntu 10.04 wouldn't cooperate with my Nvidia graphic card. I have not installed Kubuntu 10.10 in fear of overwriting my NTFS partition. Kubuntu install sees the whole harddrive (160gb) as one single partition.

Thank you

---

### Post by oldfred on 2010-10-19
Your partition table is all messed up. I would use liveCD to copy any files you have not backed up before doing anything.

```
/dev/sda2         304,869,374   312,576,704     7,707,331   5 Extended
Extended  partition  linking to another extended partition
Invalid MBR Signature found
/dev/sda5     ? 4,599,836,609 4,599,836,608                   Unknown
/dev/sda6     ? 4,599,836,609 4,599,836,608                   Unknown

/dev/sda5 ends after the last sector of /dev/sda
the logical partition /dev/sda5 is not contained in the extended partition /dev/sda2
/dev/sda6 ends after the last sector of /dev/sda
the logical partition /dev/sda6 is not contained in the extended partition /dev/sda2

```

You may be able to boot sda1, your windows if you install a windows boot loader.
Restore basic windows style boot loader - universe enabled from Ubuntu or liveCD
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

You could try using testdisk to restore partitions.
enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

