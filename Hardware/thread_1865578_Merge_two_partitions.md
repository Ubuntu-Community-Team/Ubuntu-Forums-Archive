---
title: "Merge two partitions"
date: 2011-10-20
forum: Hardware
---

### Post by algrossi on 2011-10-20
I am running a dual boot Dell laptop and I have two partitions I would like to merge:
/dev/sda1 - NTFS - Windows XP
/dev/sda2 - Extended
/dev/sda5 - NTFS - Windows XP second partition
/dev/sda6 - ext4 - empty
/dev/sda7 - ext4 - Ubuntu bootable system
/dev/sda8 - ext4 - /

I would like to merge the "Empty" and "Ubuntu" partitions.
Since I am fairly new to linux filesystem management, I need some advice on how to best approach this. I have GParted installed.
...looking for some wise words from the community.
Thank you
Al

---

### Post by jllarden on 2011-10-20
I guess you'd like to merge /dev/sda6 and /dev/sda7. Is that right?

What does 'df -h' show? I don't exactly understand what 'Ubuntu bootable system' is, maybe /boot?

---

### Post by coffeecat on 2011-10-20
Do you mean to "merge" sda6 and sda7? If they are contiguous (adjacent), you would do that by deleting sda6 and then enlarging sda7. Both partitions need to be unmounted when you do that, so you will almost certainly need to use Gparted from the live CD.

It's a bit unclear what your sda7 and sda8 partitions are. You have referred to sda8 as "/" which means the root partition, and sda7 as "ubuntu bootable system". Please post the output of these terminal commands to be sure we are not missing something important:

```
sudo fdisk -lu
sudo blkid
cat /etc/fstab
mount
```

You can highlight the output with the mouse, right-click to copy and then paste into your post. Please enclose the output between [noparse]```
 and 
```[/noparse] tags.

---

### Post by algrossi on 2011-10-20
Yes, I would like top merge sda6 and sda7. sda6 is empty and I already labeled it "Ubuntu-2", to get ready for the merge, but I am not confident enough to go any further. sda7 is the installed Ubuntu.
When I originally installed Ubuntu, sda10 was allocated as swap, when I reinstalled Ubuntu it allocated sda9 as swap, but that is not important.
I believe sda8 is orphaned and I would like to attach it to Ubuntu it if possible because it's 6GB in size.
Here is a snapshot of the result of your suggested commands:

```
=============== sudo fsisk -lu ===========================
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c4c19

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    41494738    20747338    7  HPFS/NTFS
/dev/sda2        41496574   156301311    57402369    f  W95 Ext'd (LBA)
/dev/sda5        41496637    70187984    14345674    7  HPFS/NTFS
/dev/sda6        70188048    81915434     5863693+  83  Linux
/dev/sda7        81915904   139592619    28838358   83  Linux
/dev/sda8       139593728   152457215     6431744   83  Linux
/dev/sda9       152459264   153147391      344064   82  Linux swap / Solaris
/dev/sda10      153155584   156301311     1572864   82  Linux swap / Solaris

================ sudo blkid ===========================
/dev/sda1: UUID="0A54B7BC54B7A8B9" TYPE="ntfs" 
/dev/sda5: LABEL="Win-XP-2" UUID="903272B73272A240" TYPE="ntfs" 
/dev/sda6: LABEL="Ubuntu-2" UUID="30ca1b22-6dff-4687-907b-40a46091efb6" TYPE="ext4" 
/dev/sda7: LABEL="Ubuntu" UUID="d27bad07-3cb1-439f-be02-4712ee4394ce" TYPE="ext4" 
/dev/sda8: UUID="de77721f-7258-436e-9864-47e4ce0cef04" TYPE="ext4" 
/dev/sda9: UUID="930d188b-fa00-4e39-96e9-d86db05c562f" TYPE="swap" 
/dev/sda10: UUID="6c6ce4b5-e3ff-4b59-81c3-aa49362e7629" TYPE="swap" 

======================= cat /etc/fstab =======================
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=de77721f-7258-436e-9864-47e4ce0cef04 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=930d188b-fa00-4e39-96e9-d86db05c562f none            swap    sw              0       0

========================= mount ==========================
/dev/sda8 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/algrossi/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=algrossi)
```

THank you for your quick reply;
Al;

---

### Post by coffeecat on 2011-10-20
I've added code tags for you. So much easier to read. One for your bookmarks. :wink:

[http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

> **algrossi said:**
>  sda7 is the installed Ubuntu.

Ah, but it isn't. It's not even mounted. And...

> **algrossi said:**
> I believe sda8 is orphaned and I would like to attach it to Ubuntu it if possible because it's 6GB in size.

Far from being orphaned, it's your Ubuntu root partition - check your /etc/fstab contents and mount output.

As you may wish to re-think your strategy based on that information, I'll wait until you post again before helping you with any merging of partitions. While you think this over, you might want to back up all your data. Manipulating partitions carries with it the small risk that things could go wrong. Now is the time to backup if you haven't done so already.

---

### Post by algrossi on 2011-10-20
At this point, the only partitions I want to not touch are:
/dev/sda1
/dev/sda2
/dev/sda5
these belong ro Windows-XP. Anything higher than that I can trash and re-install Ubuntu because I backed up my Ubuntu files in the Windows folder.
Perhaps this can lead to a simpler approach, I hope. I already installed Ubuntu several times because it had been many years since I touched Unix and I've learned a lot in the process.
Al;

---

### Post by coffeecat on 2011-10-20
If you're happy to reinstall, that's fine. You would need to delete sda6,7,8,9 and 10 in the live CD and then set up whatever partitions you want for Ubuntu. That would have the bonus of removing the spare swap partition. When you boot up the live CD and open Gparted, you will need to right-click on each of the swap partitions in turn and choose "swapoff" before you will be able to delete them.

Post back if you need any help with settings up a custom Ubuntu partition layout.

---

### Post by algrossi on 2011-10-20
Looks good, I booted with the install disk, deleted the partitions which  would give me enough space for Ubuntu and installed over this space. I  restored all the backups from my Windows partition back into Ubuntu.  It's almost straightforward, but for a noob like me, there was some  learning along the way, I'm very happy with the progress - 3 hours; from  trashing the whole thing to a very operational system with all the  customization I had made during my previous install.
Thank you for all the help, sometimes it's easier to have some guidance.
Have a great day;:grin:
Al;

---

### Post by coffeecat on 2011-10-20
Happy Ubuntu-ing! :)

---

