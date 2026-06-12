---
title: "unable to mount gpt fakeraid partition"
date: 2010-07-23
forum: Hardware
---

### Post by toonvl on 2010-07-23
Hi,

I have a fakeraid with 2 1,5 TB disks which I formatted on windows with a gpt table and an ntfs partition. This partition holds all my data and you can understand that I would REALLY like to access that data from Ubuntu. dmraid is installed fine and acknowledges the raid disk. But most disk-tools don't recognize the partition on it.. they just see an empty disk. Only parted is able to see the gpt table and its partitions. I've been looking around for some time now and I still haven't found anything that works. Does anyone have an idea to make Ubuntu see the partition so I can finally mount it? thanks a lot in advance!;)

(ps: I don't know if it's relevant but I used the wubi isntaller)

---

### Post by lean296 on 2012-04-13
Hi there, I'm facing some similar problem now, have you fixed yours?

What i have is a Raid 0 with 2 1.5Tb disks using the raid of the motherboard (Gigabyte GA-H55M-USB3), I partitioned the 3Tb resulting drive with windows as follows (this is from the parted has crashes a few times, gdisk works fine)

Model: Linux device-mapper (striped) (dm)
Disk /dev/mapper/jmicron_R0-Data: 3001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  2147GB  2147GB  ntfs         Basic data partition
 2      2147GB  2362GB  215GB   ntfs         Basic data partition
 3      2362GB  2523GB  161GB   ntfs         Basic data partition
 4      2523GB  2738GB  215GB   ntfs         Basic data partition
 5      2738GB  3001GB  263GB                Basic data partition

and can not find any way to mount neither the ntfs parts or create a ext4 fs on the 5th, wich i'm planning to use to store virtual machines. 

To access the ntfs file system is highly desirable.

any help will be appreciated.

---

