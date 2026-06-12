---
title: "Recreate software raid - no partitions /dev"
date: 2010-10-02
forum: Hardware
---

### Post by JackSchnippes on 2010-10-02
Hello users,


I had a software raid running (RAID 1) with 2 1TB hard disks formatted with ext3. Now I installed ubuntu server and I can't use mdadm to recreate the raid, since I don't see the partitions in /dev. the harddisks are /dev/sdb and /dev/sdc, but I don't see /dev/sdb1 and /dev/sdc1... however, when I run parted I can see that the ext3 partitons are still there!:

```
# parted /dev/sdb
GNU Parted 2.2
Using /dev/sdb
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            
Model: ATA WDC WD10EADS-00L (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      17,4kB  1000GB  1000GB  ext3         primary

``````
# parted /dev/sdc
GNU Parted 2.2
Using /dev/sdc
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            
Model: ATA WDC WD10EADS-00L (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      17,4kB  1000GB  1000GB  ext3         primary

```

```
# dmesg | grep sdb
[    2.318388] sd 2:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.318491] sd 2:0:0:0: [sdb] Write Protect is off
[    2.318497] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.318548] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.318849]  sdb: sdb1
[    2.366434] sd 2:0:0:0: [sdb] Attached SCSI disk

```

```
# dmesg | grep sdc
[    2.865843] sd 3:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.866312] sd 3:0:0:0: [sdc] Write Protect is off
[    2.866319] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.866379] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.866686]  sdc: sdc1
[    2.922201] sd 3:0:0:0: [sdc] Attached SCSI disk

```
what am I missing? is it something with the /etc/fstab and UUIDs?
thanks for any hints!

---

### Post by kotnik on 2010-10-02
You haven't built RAID matrix properly, so it doesn't get recognized. This is the output you should be seeing:

```
# parted /dev/sda
GNU Parted 2.2
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            
Model: ATA WDC WD2500JB-00R (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
 1      1049kB  1000MB  999MB   primary  ext4            boot
 2      1000MB  30.0GB  29.0GB  primary  ext4            raid
 3      30.0GB  249GB   219GB   primary  ext4            raid
 4      249GB   250GB   1058MB  primary  linux-swap(v1)
```

Pay attention to flags. I suggest backing up everything and making RAID again.

---

### Post by JackSchnippes on 2010-10-02
i did the following but I still don't get any /dev/sdb1 and /dev/sdc1... 

```

(parted) toggle 1 raid

```

```

# parted /dev/sdb
GNU Parted 2.2
Using /dev/sdb
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            
Model: ATA WDC WD10EADS-00L (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      17,4kB  1000GB  1000GB  ext3         primary  raid


```guess I'll have to do the RAID from scratch :(  maybe I can get the data somehow..

---

### Post by psusi on 2010-10-02
There is no reason to have 3 different partitions, but yes, one should be raid.

---

### Post by srs5694 on 2010-10-02
> **JackSchnippes said:**
> I had a software raid running (RAID 1) with 2 1TB hard disks formatted with ext3. Now I installed ubuntu server and I can't use mdadm to recreate the raid, since I don't see the partitions in /dev. the harddisks are /dev/sdb and /dev/sdc, but I don't see /dev/sdb1 and /dev/sdc1... 

Please clarify what you mean by this. If you type "ls /dev/sd[bc]?", what output do you see? It sounds like you're saying there's no /dev/sdb1 or /dev/sdc1 device. If that's the case, then my initial guess would be that your kernel lacks GPT support. (GNU Parted is reporting your disks use GPT, not MBR, partitions.) Ubuntu's kernel, though, does include GPT support, so this would only make sense if you've recompiled your kernel or if you're using some kernel that doesn't include GPT support.

If you do have /dev/sdb1 and /dev/sdc1 device files, then what precisely do you mean when you say that you "don't see" those devices? What program (and command in the program) is not showing them?

---

### Post by JackSchnippes on 2010-10-04
Thanks for your post. Sorry if I wasn't clear enough. What I was trying to say is that when I do "ls /dev", the files sdb and sdc are there, but sdb1 and sdc1 are not. there is nothing  like sdbx or sdcx (where x is a number). just sdb and sdc. So when I ise "ls" I can see the devices, but not the partitions.

Thanks for the hint with GPT. I will have to check on that on the weekend (machine is not with me right now). Just in case you're right, I guess GPT-support is not just a module that isn't loaded?

---

### Post by psusi on 2010-10-04
The reason the partitions do not show up is because you used the whole raw disk as the device when creating the raid, instead of a partition on the disk.  Thus the disk has no partitions.  Instead the partitions exist inside the raid array.

If you get the array started, you should be able to get the partitions recognized by running sudo partprobe /dev/md0.

---

