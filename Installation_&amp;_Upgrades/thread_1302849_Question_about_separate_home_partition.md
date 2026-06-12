---
title: "Question about separate /home partition"
date: 2009-10-27
forum: Installation &amp; Upgrades
---

### Post by donsy on 2009-10-27
In viewing this link about [how to install a separate /home partition]("http://www.psychocats.net/ubuntu/installseparatehome"). The last paragraph is puzzling:
> **Note**: Some more experienced Linux users like to have a fresh installation with every new Ubuntu release, and so will have only a separate data partition and not a separate /home partition, so all of their photos and music and documents will be preserved during a reinstallation, but all the settings will have to be redone. For novices, I would recommend just sticking with a separate /home partition. Why wouldn't someone just keep all their data under the /home directory tree which is on its own partition anyway? That way they could preserve all their settings AND their data as well. Am I missing something here?

BTW, this is what I plan to do for the 9.10 release, so if anyone knows of a better link than the one above I would appreciate it.

---

### Post by fancypiper on 2009-10-27
My preference is both!  I have a separate /home partition and a separate /pub partition.  If I want a fresh untweaked desktop, I just install with a different username.

My partitioning scheme:

Tue Oct 27 01:55 PM piper@tinwhistle ~ $ sudo fdisk -l
[sudo] password for piper: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ee220

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2612    20980858+  83  Linux
/dev/sda2            2613        2874     2104515   82  Linux swap / Solaris
/dev/sda3            2875      121601   953674627+  83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x54abb23a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux

Tue Oct 27 03:17 PM piper@tinwhistle ~ $ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sdb1 on /pub type ext3 (rw,relatime)
/dev/sda3 on /home type ext3 (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/piper/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=piper)
/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=piper)

---

### Post by davec64 on 2009-10-27
In answering your question, have a look in your /home directory using Nautlius and go to view and click show hidden files. You'll see lots of files with a full stop in from of them. These are normally hidden and will contain configuration settings for all your apps.
Now if you have a separate /data partition all your data is separate from your configuration files, so when you upgrade doing a fresh install new settings will be created.
Hope that explains it!

Personally /home is enough for me!  :)

---

### Post by chathamsq on 2009-10-27
The author is talking about a scenario where the user *wants* his/her settings & configuration to be overwritten with defaults for each new release, but also wants to preserve his/her documents, etc.  In this scenario, the documents are kept on a separate partition (so that they are preserved), and the home directory is located on the root partition (which will be overwritten by the new release).

I personally keep a separate home partition, so I can only guess as to why one would want that setup.  One thought is that the new Ubuntu release would include newer versions of some applications, and the user may want to customize these from scratch rather than carrying forward their existing settings.  This of course creates more work for the user to repeat all their customizations.

Generally a separate home partition is appropriate for most users; I'd only go the other way if you had a specific reason for doing so.

---

