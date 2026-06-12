---
title: "Partition table is not read"
date: 2008-11-27
forum: Hardware
---

### Post by dev.null on 2008-11-27
Summary:

1. server lts install.
2. initial install didn't recognize raid partitions, after installing raid tools the raid partitions were assembled, mounted, and accessed without a problem.
3. after reboot the kernel couldn't 'see' the raid partitions any more, although cfdisk and sfdisk --dump still showed the partitions.



I setup a system several years ago, P3 294M RAM, 4 disk install -

sda1 20G ext3 mounted to /

sdb1 80G linux raid disk 1
sdc1 80G linux raid disk 2
sdd1 80G linux raid disk 3

the 3 raid disks combine into 1 raid5 mounted as /mnt/md0.

The user kept turning the box off whenever they thought it was hung and eventually the sda1 wouldn't fsck when boot from that disk.

I figured since there was going to be some down time I'd go ahead and upgrade the OS and primary drive. I went with ubuntu server lts.

To install I disconnected the three raid drives, replaced sda with a 160G disk, and connected up a CD rom w/ the server install (P3 wouldn't boot off of usb install stick I usually use). Install went fine. I disconnected the cdrom and reconnected the raid disks and booted back up. I had to apt-get install the raid tools, when I ran mdadm --auto-detect it picked up the raid drives and after mounting the raid it all checked out - cat /proc/mdstat showed the raid5 with all 3 good drives. I mounted it to /mnt/md0 and checked the files out - everything was good to go.

Then I rebooted...

When it booted up md0 wasn't there. Looking through the syslog I could see where md0 would would unbind drives and end up not running.

Here's the crazy part. When I cfdisk and sfdisk --dump I can see all the partition tables correctly. When I ls /dev/sd* and cat /proc/partitions neither has /dev/sdb1 or /dev/sdd1. They do show /dev/sda1 and /dev/sdc1, just not sdb1 or sdd1.

I couldn't figure it out. No matter what I tried (like parted and hdparm -z /dev/sdb) it would never recognize the first partition of either sdb or sdd even though they would show the disks, just not the partitions.

I've ended up just fsck'ing the old original 20G and booting with the old FC3 (sigh). It works, but I would rather have been able to stick with ubuntu.

Any ideas?

---

