---
title: "Can't change hard drive permissions"
date: 2009-09-12
forum: Hardware
---

### Post by Feanor93 on 2009-09-12
Hi, I'm a bit of a noob at this, so I don't know if this is the right category for this post, but my problem is hardware related so here goes:

I recently just installed a 1Tb SATA hard drive in my computer. The only problem is that it's owned by the root account, and I can't change the drive's permissions even if I log into root. If anyone could shed some light on this I would be grateful (it kinda stinks to have to log into root whenever you want to write to the disk).

Thanks,
Feanor93

---

### Post by ajgreeny on 2009-09-12
You can set the permissions for the drive with the lines in /etc/fstab relating to the drive.  Show us what you have at the moment with ```
cat /etc/fstab
```in terminal and copy the output back here.

The line you need should look like this, but with the dev name for your system and similarly the mount point:-
**/dev/sdb /media/diskname ext3 defaults,relatime 0 2**

---

### Post by Feanor93 on 2009-09-14
Here is the output I got:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=d825de03-3308-4aba-984c-f738ab15e759 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=c6133fb0-b50a-42d4-9893-8fb73c302e9b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0    *
/dev/sdb1    /media/TheBigOne   vfat    defaults     0        2"TheBigOne" is my terabyte drive.

---

### Post by ajgreeny on 2009-09-14
OK, I didn't even think about the fact that it would be a fat32 drive.  You have two main options:-
1-   Edit the line in fstab to read
```
/dev/sdb1 /media/TheBigOne vfat defaults,user,exec,uid=1000,gid=100,umask=000 0 0
```
2-    remove that line completely, format the drive to ntfs using gparted on the live CD, and then use ntfs-config and ntfs-3g, which you may need to install from the repos, to set the read/write capabilities as you want.

---

### Post by Feanor93 on 2009-09-14
I'm afraid I don't know how to edit the line. Could you just briefly tell me how to do that?

---

### Post by ajgreeny on 2009-09-14
In terminal type ```
gksudo gedit /etc/fstab
``` enter password when asked (it will not show in the terminal) and then edit the file as normal and save.  By default gedit will make a backup of the file so if it all goes wrong you can get the original back.  After the edit enter ```
sudo mount -a
```in terminal and the disk should now be available to you if you left it as a fat32 disk.  If you deleted the line and formatted to ntfs and installed the ntfs packages, just reboot.

---

### Post by Feanor93 on 2009-09-14
It's working fine now.

Thanks!
Feanor93

---

