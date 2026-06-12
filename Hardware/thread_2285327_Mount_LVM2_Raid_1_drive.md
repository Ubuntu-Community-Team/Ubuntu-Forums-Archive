---
title: "Mount LVM2 Raid 1 drive"
date: 2015-07-04
forum: Hardware
---

### Post by thatcanadiannerd on 2015-07-04
I have an Iomega NAS device that worked poorly and I am trying to access the data without the enclosure but rather directly from the drive now plugged into my computer. I have discovered that it is formatted in LVM2 PV Raid 1 and I am unable to mount it regularly. The following discussion in the Arch linux forum is very similar to what I have been experiencing but I have only TRIED to use Arch once and I do not understand alot of the discussion:[https://bbs.archlinux.org/viewtopic.php?id=144098](https://bbs.archlinux.org/viewtopic.php?id=144098)
How can I mount this drive in ubuntu to access the files (I am running ubuntu on a live USB and I have a very limited understanding of different Linux commands and systems)
the command: [COLOR=#070F14][FONT=Verdana]sudo lshw -C disk returned:
[/FONT][/COLOR][COLOR=#070F14][FONT=Verdana]description: ATA Disk[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]product: ST32000542AS[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]vendor: Seagate[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]physical id: 0.0.0[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]bus info: scsi@2:0.0.0[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]logical name: /dev/sdb[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]version: CC38[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]serial: 5XW2LJDC[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]size: 1863GiB (2TB)[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]capabilities: gpt-1.00 partitioned partitioned:gpt[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]configuration: ansiversion=5 guid=97467a0b-2782-4d4e-afca-912d89da9338 se

[/FONT][/COLOR][COLOR=#070F14][FONT=Verdana]Any help would be super appreciated!!!

[/FONT][/COLOR]

---

### Post by weatherman2 on 2015-07-04
Open a terminal and type these commands and report their output here:

```
sudo pvdisplay
sudo vgdisplay
sudo lvdisplay

```

---

### Post by thatcanadiannerd on 2015-07-05
The following is the output I recieved from these commands:
ubuntu@ubuntu:~$ sudo pvdisplay
ubuntu@ubuntu:~$ sudo vgdisplay
  No volume groups found
ubuntu@ubuntu:~$ sudo lvdisplay
  No volume groups found
ubuntu@ubuntu:~$ 

am I doing something wrong or is it because the drive is not mounted?

---

### Post by weatherman2 on 2015-07-05
You don't technically mount "drives," you mount partitions or volumes.  If this drive uses LVM, then it has logical volumes, and you would mount the logical volumes to access them.

If no volume groups are round, then Ubuntu is not detecting the LVM at all.  There's nothing to mount.

Try this command:

```
sudo parted -l
```

which should list all partitions on the drive.

---

### Post by steeldriver on 2015-07-05
+1 to parted: if the LVM is on top of RAID, as suggested in your first post, then you will need to assemble the RAID first I think

---

### Post by thatcanadiannerd on 2015-07-05
Oh I see, here is what it returned for that command:
Model: ATA ST32000542AS (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      33.6MB  21.5GB  21.5GB               primary  raid
 2      21.5GB  2000GB  1979GB               primary  msftdata


Error: /dev/sdc: unrecognised disk label                                  

Model: SanDisk Cruzer U (scsi)
Disk /dev/sdd: 16.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  16.0GB  16.0GB  primary  fat32        boot, lba

---

### Post by thatcanadiannerd on 2015-07-05
> **steeldriver said:**
> +1 to parted: if the LVM is on top of RAID, as suggested in your first post, then you will need to assemble the RAID first I think

I'm sorry I am not sure what you mean by "+1 to parted" but to my best understanding the RAID is located inside the LVM2 PV partitioning system so how would I assemble the raid so I can just deal with the LVM2 system? some of the commands I found to run said it was RAID 1 but I thought that meant all data takes twice the space (miroring) which I had not noticed on the drive? This is merely my understanding correct me where I am wrong!

---

### Post by weatherman2 on 2015-07-05
(I assume by "+1 to parted" he meant he agreed with my suggestion for running the parted command - like liking a post on Facebook or Google Plus.)

According to your parted output, you have two partitions on that drive: a small 21.5GB "raid" partition and a large 1979GB Windows partitions (presumably NTFS).  Is the data that you want really on that small partition?  If so, you can try building an array using /dev/sdb1 with the mdadm command.  

If you think you want the data from the big Windows partition, try this:

```

sudo mount /dev/sdb2 /mnt
ls /mnt

```

I too haven't used mdadm for a while - but you can find guides to use it easily by web searching.  That's what I would do if I were trying to build a RAID with that disk.

---

### Post by weatherman2 on 2015-07-05
And FYI, a RAID 1 (mirror) would be on two separate disks.  There's no benefit of building a RAID mirror with two volumes or partitions on a single disk, because the main reason for using a RAID mirror is to protect yourself against hard drive failure.  A partition on a NAS drive could be set as RAID with only one member volume with the idea that you could add another drive to it in the future to make a real RAID mirror.

---

### Post by thatcanadiannerd on 2015-07-05
Ok gotcha! Yeah I want access to the large partition but when I try the mount command "sudo mount /dev/sdb2 /mnt it returns "mount: unknown filesystem type 'linux_raid_member'" so thats when I figured out about the LVM2 and raid correct me if I am wrong but I assumed that the LVM2 allowed the RAID to be in both partitions and therefore it was necessary to deal with the LVM2 then the raid and I would then be able to mount it

---

### Post by thatcanadiannerd on 2015-07-05
> **weatherman2 said:**
> And FYI, a RAID 1 (mirror) would be on two separate disks.  There's no benefit of building a RAID mirror with two volumes or partitions on a single disk, because the main reason for using a RAID mirror is to protect yourself against hard drive failure.  A partition on a NAS drive could be set as RAID with only one member volume with the idea that you could add another drive to it in the future to make a real RAID mirror.

Oh I see thanks that makes alot of sense!

---

