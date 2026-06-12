---
title: "Using MDADM to add RAID 1 setup to existing data drive"
date: 2011-03-09
forum: Hardware
---

### Post by Trebacz on 2011-03-09
I'm adding a new data hard drive to an existing kubuntu 10.10 system. The system currently has a 2 hardrives installed:

[LIST]
[*]250GB boot, system, and swap drive
[*]1TB data drive (no system information)
[/LIST]
I'd like to add another 1TB drive to mirror (RAID 1) my existing data drive and softraid it. The data on the drive is backups of other machines, so I could lose it and only be out some old backups.

Although my motherboard supports fakeraid, I've been convinced by several other articles that I'm probably best off going with linux mdadm setup. I'm not dual booting into windows.

I found an older article on the process and the process sounds okay. I would appreciate any comments before I try it, especially if there are any Ubuntu specific issues I may run into. The steps from the other article are:

A: If you are trying to mirror a data drive. Assumption, existing data drive is /dev/sdb and new drive is /dev/sdc.

1. Make sure your kernel had RAID support and both md_mod & raid1 modules are loadable.
2. With fdisk, create a new partition of type fd on your new drive.
3. Initialize a degraded RAID1 array: mdadm -C /dev/md0 --force --level=1 --raid-devices=2 /dev/sdc1 missing.
4. Create a filesystem on /dev/md0: mkfs -t ext3 /dev/md0.
5. At this point, /dev/md0 is fully usable. Mount /dev/md0 and copy the contents of /dev/sdb to /dev/md0.
6. Unmount /dev/sdb and mount /dev/md0 in /dev/sdb mount point.
7. With fdisk, repartition /dev/sdb with a partition of type fd.
8. Add /dev/sdb1 to your existing RAID1 array: mdadm /dev/md0 --add /dev/sdb1. *I encountered a problem with adding the old drive to the array this morning if I didn't create a filesystem on it first. I don't recall doing this the last time.
9. Array will now start to rebuild. Use mdadm -D /dev/md0 to check its rebuild status.
10. Edit your /etc/fstab file and edit all references of /dev/sdb to /dev/md0.
* No reboot is required.

Here is the link to the full thread:
[Disk Mirroring in Linux]("http://www.tek-tips.com/viewthread.cfm?qid=1318503&page=1")

---

### Post by HankB on 2011-03-09
I've done that and it worked fine. The only thing I would add is that you have to install mdadm. All Ubuntu kernels I've used include MD support but the admin tools are not installed by default.

In step 8, I have no recollection of creating the file system before adding the second drive to the RAID.

I also backed up to an external drive first. ;)

Good luck!

-hank

---

