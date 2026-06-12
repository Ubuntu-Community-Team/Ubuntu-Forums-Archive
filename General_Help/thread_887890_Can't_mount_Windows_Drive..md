---
title: "Can't mount Windows Drive."
date: 2008-08-12
forum: General Help
---

### Post by apreichner on 2008-08-12
Alright so I had Ubuntu 7.10 Gutsy installed and everything worked great. I just installed Ubuntu 8.04 Hardy Heron (32-bit) because one of the programs I wanted to install wasn't compatible for Gutsy. After the installation finished, I could no longer find my 80gb Windows Drive that i was previously able to mount on Gutsy. So of course the first thing I did was go into Terminal and do the fdisk -l command, and I got this.

```
alan@alan-desktop:~$ sudo fdisk -l
[sudo] password for alan: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf92ff92f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

```

Which is the drive that i want. So I went ahead and tried to follow some NTFS-3g mounting instructions. (Put the drive in my fstab and do the mount -a command) and I got this.

```
alan@alan-desktop:~$ sudo mount -a
ntfs-3g: Failed to access volume '/dev/sda1': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.

```

At that point I was pretty stumped. I mean it worked fine in Gutsy and my 2 other NTFS drives work fine, just not this one. Any help would be greatly appreciated.

---

### Post by theyranos on 2008-08-12
What does your fstab look like?

Also, (total shot in the dark here) are you sure the mountpoint is still there?

---

### Post by WRDN on 2008-08-12
In the terminal, type:

```

sudo mkdir /media/[name]

```

Replace "[name]" with the folder you want to mount the drive in (e.g. /media/windows)

Now, type:

```
sudo mount /dev/sda1 /media/windows/
```

To unmount the partition:

```
sudo umount /media/[name]/
```

---

### Post by apreichner on 2008-08-12
> **WRDN said:**
> In the terminal, type:

```

sudo mkdir /media/[name]

```

Replace "[name]" with the folder you want to mount the drive in (e.g. /media/windows)

Now, type:

```
sudo mount /dev/sda1 /media/windows/
```

To unmount the partition:

```
sudo umount /media/[name]/
```

I tried this and I get this error in the terminal. 

```
alan@alan-desktop:~$ sudo mkdir /media/Windows
[sudo] password for alan: 
mkdir: cannot create directory `/media/Windows': File exists
alan@alan-desktop:~$ sudo mount /dev/sda1 /media/Windows/
mount: special device /dev/sda1 does not exist

```

My fstab looks like this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=1f7ac43a-8447-4ec9-9d08-8b0ca0f030d7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=da5c0d6f-0ebf-4a5e-bf81-d49e05d9aa1a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda1     /media/Windows     ntfs-3g     defaults,locale=en_US.utf8   0    0
```

I added the bottom line myself earlier when I was following ntfs-3g mount instructions.

---

### Post by theyranos on 2008-08-12
What happens if you
```

sudo partprobe -s

```

and then try the 
```

sudo mount -a

```
again?

---

### Post by apreichner on 2008-08-12
> **theyranos said:**
> What happens if you
```

sudo partprobe -s

```

and then try the 
```

sudo mount -a

```
again?

That worked great! Thanks a lot for your help. It works now.

---

