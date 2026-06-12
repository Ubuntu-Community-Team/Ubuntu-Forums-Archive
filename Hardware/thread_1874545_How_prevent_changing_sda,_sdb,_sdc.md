---
title: "How prevent changing sda, sdb, sdc?"
date: 2011-11-03
forum: Hardware
---

### Post by Azyx on 2011-11-03
During boot different drives get asigned different. Sometimes my SATA 250GB disk be dev/sda and my two PATA 300GB being /dev/sdb and /dev/sdc. Other times my PATA disk being asigned /dev/sda and /dev/sdb and my SATA /dev/sdc.
I think Linux(Ubuntu)  have 'solved' that problem with UID, but to get a UID it's need to be a partition on it and it't the partition who get the UID. Or?

Are that not a problem with filesystem there you don't have to partition the disk for instance zfs or btrfs?

---

### Post by oldfred on 2011-11-03
We have seen that with mixed PATA/SATA systems. My SATA only system is always consistent, but even a flash drive may get mounted at different places depending on what other devices I have used.

The UUID allows Ubuntu/grub to boot the correct partition. I thought all file systems worked better with partitions. Just using a drive without a partition is not really recommended as everything is partition dependant. If only using Linux, you may want the newer gpt partitioning, but Windows can only use gpt with UEFI (not BIOS) boot.

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)

If drive is only going to be Ubuntu (never Windows), I would suggest using gpt not MBR as the partitioning scheme. You then do not have any logical partitions, they are all primary and it has a backup in case of problems. You do have to create a tiny bios_grub partition to correctly install grub2's boot loader to the drive.
If using gpt create a 1MB bios_grub partition at the beginning of the drive. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning.

GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

---

### Post by Azyx on 2011-11-03
Thanks oldfred for your information :)
If we forgott boot problems and just look at how the systems recognize similar disks. I have under some occations tried to set up raid, on a computer with both SATA and PATA. Last time  just the last day. I asigned two of my disks as [COLOR=Red]dev/sda1[/COLOR] and [COLOR=Blue]dev/sdb1[/COLOR] (PATA) in the raid-utility ([COLOR=DarkGreen]mdadm[/COLOR]) as raid1. It take severals hours to synconise the disks, but when it was ready I add /dev/md0 to mount in /home/Azyx/300GB in fstab and a 'sudo mount -a', and the drive worked fine :). But when I reboot, the system stoped cos it could not mount my raid :(. When I get in in the disk utility it said the raid was broken and tried to repair :(. And then when I look at device-name it was changed to [COLOR=Red]dev/sdb[/COLOR] and [COLOR=Blue]/dev/sdc[/COLOR]. Could that be the problem?

It take so long time to get raids to be created, so I what to really now what I'm doing. Could it be better to use UID in the raid-utility ([COLOR=DarkGreen]mdadm[/COLOR]) instead of /dev/sdx1?

Another thing is that both zfs and btrfs don't what formated disks before the diskutilities make them. you asign the disks /dev/sdx, not partitions /dev/sdx1, for best results. I think.

Thanks again for your advise :)

/Cheers

---

### Post by WasMeHere on 2011-11-03
Yes, using **UUID** in /etc/fstab makes the system always mount the partitions as you want them mounted.

Another option is to give the partitions a **label** (can be done easily with gparted, of course from a live disk). Then you use the label in /etc/fstab.

I haven't used RAID, but it seems reasonable that the same methods should work to identify the partitions.

---

### Post by Azyx on 2011-11-03
> **Olle Wiklund said:**
> Yes, using **UUID** in /etc/fstab makes the system always mount the partitions as you want them mounted.

Another option is to give the partitions a **label** (can be done easily with gparted, of course from a live disk). Then you use the label in /etc/fstab.

I haven't used RAID, but it seems reasonable that the same should methods should work to identify the partitions.

Do RAIDs have any UID? I forgot to check it, and now I erased it, cos mybee I'll try btrfs mirrow instead. But don't want to know before I test. It's take so long time for the system to synk. To make btrfs, you cannot use gparted or disk-utilities. It a hole new type of thing.

---

### Post by WasMeHere on 2011-11-03
If you ***cannot find another method *** than to identify the disks by their device IDs (/dev/sda1 ...) when you set up RAID, you cannot have 'changing sda, sdb, sdc'. Then the simple solution is to avoid mixing PATA and SATA disks. (I had a brief look at a couple of tuturials, and there was no option to use any other method.)

---

### Post by Azyx on 2011-11-03
> **Olle Wiklund said:**
> If you ***cannot find another method *** than to identify the disks by their device IDs (/dev/sda1 ...) when you set up RAID, you cannot have 'changing sda, sdb, sdc'. Then the simple solution is to avoid mixing PATA and SATA disks. (I had a brief look at a couple of tuturials, and there was no option to use any other method.)

But that solution require major purchase of hardware. I don't have money, but time ;). Another solution could be to use freeBSD or other, that assign harwere depending on where they are placed in the computer, IDE-channel 1 or 2 etc. I have started a new creation of raid and it will be ready till tomorrow and check it out. I will also check out what [COLOR=Red]oldfred[/COLOR] said. Maybe grub2 could be a help to do the assigning even for disks/partition that not are boot-partionons/disk and get then right?

---

### Post by oldfred on 2011-11-03
I know so little about RAID that I cannot really help. I know Ubuntu/grub changed to UUIDs to avoid the issue, but do not know about RAID.

Why RAID? Many think it is a backup and it is not. It provides some speed advantage if configured some ways, but can be slower configured other ways.  The only worthwhile RAID to me is a full (read more expensive) hardware RAID with many drives. I thing that is RAID 5 or so. Most desktops do not really need RAID, but do need better ways to back up data.

---

### Post by Azyx on 2011-11-04
> **oldfred said:**
> I know so little about RAID that I cannot really help. I know Ubuntu/grub changed to UUIDs to avoid the issue, but do not know about RAID.

Why RAID? Many think it is a backup and it is not. It provides some speed advantage if configured some ways, but can be slower configured other ways.  The only worthwhile RAID to me is a full (read more expensive) hardware RAID with many drives. I thing that is RAID 5 or so. Most desktops do not really need RAID, but do need better ways to back up data.

RAID1 or mirroring are not faster, but if one hdd get broken, you can change to a new one (i have one spare hdd) and still have your data(reducdance). raid0 on the other hand are for speedperformance and if one get broken u lost you data. To have software-raid are better than normal-prize hardware raid (that are on many motherboard and raid-card below appox 200$. My intend is to have this as a backup-server for important data. I have also an usb-disk as backup. the problem with raid5 is for PATA that you should only have one hdd/channel and most of normal motherboard only have 2. But for real storage are zfs or btrfs better cos they also have checksum-test. On the other hand, I have not have any visable data-coruption, since a leave window, there I noted that some moves hade being bad, and also some picture. That was one reason I leave windows.

---

