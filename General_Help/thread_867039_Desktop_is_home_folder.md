---
title: "Desktop is home folder"
date: 2008-07-22
forum: General Help
---

### Post by Naddiseo on 2008-07-22
Simple question: nautilus has made my desktop folder the same as my home folder, how do I change it back to ~/Desktop ?

After some searching I found /app/nautilus/preferences/desktop_is_home_dir but this was already unchecked. I tried checking it, rebooting, then unchecking it, rebooting, but I still have my home folder being my Desktop folder.

I think this probably occurred because ~/Desktop is a symlink to another folder in another partition (because I have multiple Ubuntu installations) and when I first booting the symlink was broken as the other partition wasn't mounted. 

Is this a bug, or by design?

Thanks.

---

### Post by Rocket2DMn on 2008-07-22
I've never seen this done before, but I guess it's possible to do.  I would unlink the folders so that you have your own Desktop on this installation, but if you want to keep it as it is, you need to fix the mounting problem.  I believe it is normal for broken links to revert to your home folder.
If you want to troubleshoot the mounting issue, please post the output of
```
sudo fdisk -l
cat /etc/fstab
sudo blkid
mount
```

---

### Post by Naddiseo on 2008-07-22
> I would unlink the folders so that you have your own Desktop on this installation, but if you want to keep it as it is, you need to fix the mounting problem. I believe it is normal for broken links to revert to your home folder.

The strange thing is that after the first boot I fixed the mounting and they're linking properly.


```
richard@richard-64:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00089a03

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  83  Linux
/dev/sda2               5         265     2096482+  82  Linux swap / Solaris
/dev/sda3             266       14235   112214025    5  Extended
/dev/sda4   *       14236       19456    41937682+   7  HPFS/NTFS
/dev/sda5             266        1570    10482381   83  Linux
/dev/sda6            8098       14235    49303453+  83  Linux
/dev/sda7            1571        8097    52428096   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x863a9885

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001   83  Linux

```

```

richard@richard-64:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=99f5c353-ff1c-44b3-89f3-a8760c7f4514 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=52ee531f-7176-4c3f-b69f-e56676838c17 /media/common   ext3    relatime        0       2
# /dev/sdb1
UUID=f118d2a9-8fdd-4dbd-b757-6f4cac0ee4e5 /media/usbd     ext3    relatime        0       2
# /dev/sda4
UUID=17105A187DFE7B1A /windows        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=3c789f75-2d31-453f-aca5-53c078a6fccf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```
```

richard@richard-64:~$ sudo blkid 
/dev/sda1: UUID="f97ff70e-1007-4cba-8d19-91f005d4103c" TYPE="ext2" 
/dev/sda2: TYPE="swap" UUID="3c789f75-2d31-453f-aca5-53c078a6fccf" 
/dev/sda4: UUID="2C74C8DC74C8AA42" TYPE="ntfs" 
/dev/sda5: UUID="99f5c353-ff1c-44b3-89f3-a8760c7f4514" TYPE="ext3" 
/dev/sda6: UUID="52ee531f-7176-4c3f-b69f-e56676838c17" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="54d89d83-4713-4abb-8705-2a87680e6867" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="f118d2a9-8fdd-4dbd-b757-6f4cac0ee4e5" SEC_TYPE="ext2" TYPE="ext3" 

```

```

richard@richard-64:~$ mount
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/dev/sda6 on /media/common type ext3 (rw,relatime)
/dev/sdb1 on /media/usbd type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/richard/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=richard)

```

---

### Post by Rocket2DMn on 2008-07-22
Oh, and where is the link going (what partition)?  There are a couple of entries not present in fstab, so if the link for the Desktop folder is on one of them, it won't be mounted until after you log in.  If an entry DOES exist in fstab, it should be mounted before you login, so the Desktop folder should already be in place.

---

### Post by Naddiseo on 2008-07-22
It links to /dev/sda6/ -> /media/common 

The entries not in fstab are for my gentoo partition and its /boot partition (which I need to get working)..

---

### Post by Rocket2DMn on 2008-07-22
OK, that is already listed in fstab with UUID=52ee531f-7176-4c3f-b69f-e56676838c17
You said it's linking properly now, so is everything working correctly then?

---

### Post by Naddiseo on 2008-07-22
Nope, that's my problem. All the links are working, but it's still showing my homefolder as my desktop.

---

### Post by Rocket2DMn on 2008-07-22
The problem may be that you don't have access to the shared folder.  Even if you have the same username, the uids must be the same (the first user in Ubuntu is uid 1000, but different distros can vary this).
You can feel free to fiddle with it, but it's not generally suggested to share key directories like this.  I have heard of people sharing their entire home folders between installations, but even this can create problems.

---

### Post by schnauzer93 on 2008-07-22
whoops, didn't see you already tried that.

---

### Post by Naddiseo on 2008-07-23
Well, thanks for your help but I couldn't get it working. So, I reinstalled, this time I'm not symlinking the Desktop folder, so it shouldn't happen again.

---

### Post by number nine on 2008-08-04
For those people (like me) who stumble across this thread with the same issue, I found a solution:

[https://bugs.launchpad.net/ubuntu/+bug/151576/comments/3](https://bugs.launchpad.net/ubuntu/+bug/151576/comments/3)

If Gnome can't read your Desktop, it seems to change your XGD_DESKTOP_DIR to $HOME in ~/.config/users.dirs.dirs . Change it back to $HOME/Desktop and you should be back in business - at least, it worked for me.

---

### Post by hormati on 2008-08-09
Dude, you are awesome :D
I've been looking for this since last week. This works perfectly.

Thanks
Amir

---

