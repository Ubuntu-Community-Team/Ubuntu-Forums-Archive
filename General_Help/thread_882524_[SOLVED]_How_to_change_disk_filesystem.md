---
title: "[SOLVED] How to change disk filesystem"
date: 2008-08-07
forum: General Help
---

### Post by /////// on 2008-08-07
Is there a way to change the file system of a drive without formatting everything on it. When I installed Ubuntu, I selected ext2 as the filesystem for the partition it was to be installed on however now I want to change it to ext3. Is there a way to do this without erasing everything on the partition? If this isn't possible, is there a way to backup the partition so that everything that was on the partition before is EXACTLY the same? I want all my settings, configurations, backgrounds, saved passwords etc to be exactly the same.

---

### Post by cdtech on 2008-08-07
You can use the "tune2fs" command:
login as root.
sudo -i

Unmount the /dev/sdb2 partition.
umount /dev/sdb2

If it doesn't unmount, then remount it as read-only.
mount -o remount,rw /dev/sdb2

Convert to ext3
tune2fs -j /dev/sdb2

Edit your /etc/fstab and in the /dev/sdb2 entry, change ext2 to ext3.
reboot

I have not tried this but according to the "man tune2fs" and others it does work.

Be sure to backup before you do any major partition manipulations.

Hope this helps.........

---

### Post by /////// on 2008-08-07
Does this work even if the partition I'm trying to convert is the filesystem (root (/)) partition?

---

### Post by Rocket2DMn on 2008-08-07
I've never tried any of this, but in order to fiddle with any partition it must be unmounted first.  Since you can't unmount your root filesystem, you need to boot into the Ubuntu LiveCD and perform the task(s) from there.
You should always back up your important data before fiddling with partitions, in case something goes wrong (but mostly in case you screw something up).

---

### Post by cdtech on 2008-08-07
Per the "tune2fs" man page:
> If this option is used to create a journal on a mounted filesystem, an immutable file, .journal, will be created in the toplevel directory of the filesystem, as it is the only safe way to create the journal inode while the filesystem is mounted. While the ext3 journal is visible, it is not safe to delete it, or modify it while the filesystem is mounted; for this reason the file is marked immutable. While checking unmounted filesystems, e2fsck will automatically move .journal files to the invisible, reserved journal inode. For all filesystems except for the root filesystem, this should happen automatically and naturally during the next reboot cycle. Since the root filesystem is mounted read-only, e2fsck must be run from a rescue floppy in order to effect this transition. On some distributions, such as Debian, if an initial ramdisk is used, the initrd scripts will automatically convert an ext2 root filesystem to ext3 if the /etc/fstab file specifies the ext3 filesystem for the root filesystem in order to avoid requiring the use of a rescue floppy to add an ext3 journal to the root filesystem.

---

### Post by hyper_ch on 2008-08-07
just make sure to have backups.

---

### Post by /////// on 2008-08-07
I found a guide online to help me do this:
Converting the / directory
First, think long and hard before deciding to convert the root directory. Ext3's primary purpose is shorter recovery from disaster rather than data loss prevention. Converting the root directory from Ext2 to Ext3 isn't difficult, but converting it back from Ext3 to Ext2 is a treacherous process fraught with problems. But, if you really must perform the Ext2 to Ext3 conversion on the root directory, here's how, assuming /dev/hda2 is mounted as the root directory and /dev/hda1 is mounted as /boot:

    * Log in as root
    * Edit /etc/fstab and change ext2 to  ext3 on the line referencing the root directory.
    * tune2fs -j /dev/hda2
    * cd /boot
    * mv initrd-2.4.18-26.8.0.img initrd-2.4.18-26.8.0.img.ext2
    * mkinitrd initrd-2.4.18-26.8.0.img 2.4.18-26.8.0
    * reboot

In the preceding, you MUST perform all the steps, including the mkinitrd, before rebooting. Failing to perform all the steps before rebooting produces a "buried shovel" where if only you could boot the machine, you could run the mkinitrd command, and if only you could run the mkinitrd command, you could boot the machine. 

However, in this guide, it says to use the mkinitrd command which my computer cannot find. This is also not in Synaptic Packet Manager. Is this because the guide is too old and the command has changed to something else? If it is please help. Apparently according to this guide, I can't restart or power off my machine or else I'll get this 'buried shovel'

---

### Post by /////// on 2008-08-07
Wait dw, I changed the file system. Apparently all I had to do was change the fstab file then do the tune2fs command. The reboot apparently didn't damage my compauter and now when I type mount in terminal, it shows my sda1 mounted as ext3

---

