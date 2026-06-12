---
title: "Mount or unmount FAT32"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by maurolust on 2009-03-22
Hi. This is the second time I'm trying Ubuntu (actually I'm installing it for my mother in law).

I have a dual boot with Vista and this is my partition table:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=0ae7b694-2eeb-4227-b754-74a03ad6709e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda9
UUID=304cdeda-eacb-4304-84cf-c584e4265bac /boot           ext3    relatime        0       2
# /dev/sda2
UUID=F0B25E44B25E0F88 /dos            ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=d3786d96-615d-4a1f-b55a-c71ef8ef912b /home           ext3    relatime        0       2
# /dev/sda7
UUID=1170-4127  /windows        vfat    utf8,umask=007,gid=46 0       1
# /dev/sda8
UUID=869feb2b-7b47-459d-a8b0-dfa54dcf04b3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

I probably misinterpreted something during install, and because of that I can't use the FAT32 partition. (dev/sda7) During installation I checked the option ``use it as \windows'' thinking this meant it would show in 'places' under the name 'windows', but I don't see it at all. What should I do to have access to it?
The partition where I have vista installed is labeled '/dos' and I can't have access to it either (and I guess this is desirable). What really scares me is that I can open the WinRe volume. Isn't this awfully unsafe?

How do I hide the Windows Register partition and show the FAT32 one under the Places tab?

---

### Post by ddrichardson on 2009-03-22
> **maurolust said:**
> Hi. This is the second time I'm trying Ubuntu (actually I'm installing it for my mother in law).

I have a dual boot with Vista and this is my partition table:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=0ae7b694-2eeb-4227-b754-74a03ad6709e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda9
UUID=304cdeda-eacb-4304-84cf-c584e4265bac /boot           ext3    relatime        0       2
# /dev/sda2
UUID=F0B25E44B25E0F88 /dos            ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=d3786d96-615d-4a1f-b55a-c71ef8ef912b /home           ext3    relatime        0       2
# /dev/sda7
UUID=1170-4127  /windows        vfat    utf8,umask=007,gid=46 0       1
# /dev/sda8
UUID=869feb2b-7b47-459d-a8b0-dfa54dcf04b3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```I probably misinterpreted something during install, and because of that I can't use the FAT32 partition. (dev/sda7) During installation I checked the option ``use it as \windows'' thinking this meant it would show in 'places' under the name 'windows', but I don't see it at all. What should I do to have access to it?
The partition where I have vista installed is labeled '/dos' and I can't have access to it either (and I guess this is desirable). What really scares me is that I can open the WinRe volume. Isn't this awfully unsafe?

How do I hide the Windows Register partition and show the FAT32 one under the Places tab?
These types of partition are inherently insecure and rely on a driver in Windows to hide them. So just don't mount it, if you don't want anyone in it.

/windows is the folder in the file system you've told it to put the windows drive - so it should be there prividing its mounted, if you open a terminal and type```
ls /windows
```is it there.

---

### Post by hexanol on 2009-03-22
> **maurolust said:**
> I have a dual boot with Vista and this is my partition table
Actually this is your /etc/fstab file, which is not the same. ;)

What's the output of "mount" and "ls /windows". It looks like your FAT file-system is mounted but you just didn't see it.

As for placing a shortcut in "Places", try editing .gtk-bookmark (in your home directory) and add a line similar to "file ///windows Windows". Something like that.

---

### Post by vanadium on 2009-03-22
It is easier than that. Navigate, using nautilus file manager, to /windows (select "File system" under Places, then double-click the "windows" folder. Bookmark - Add bookmark (Ctrl+D) will add it to "Places".

---

### Post by maurolust on 2009-03-23
output of 'mount':
```
vera@vera-laptop:~$ mount
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
/dev/sda9 on /boot type ext3 (rw,relatime)
/dev/sda2 on /dos type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda6 on /home type ext3 (rw,relatime)
/dev/sda7 on /windows type vfat (rw,utf8,umask=007,gid=46)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/vera/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=vera)

```

output of ls /windows:
```
vera@vera-laptop:~$ ls /windows
filme  Fotos  HDDRecovery  Musica Vera  $recycle.bin

```

I guess this is good, it means my files are there

Let me clear out what I want: I want to hide the WinRE volume (i think that is sda1, is that right?) and show what I (mis)labeled /windows (sda7). /windows should be the volume where Vista is installed, right? I put that volume (sda2) as /dos, is there a problem with that?

Thank you all for your answers so far. Here is the partition table nice and clean ;):

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2             192        5663    43945312+   7  HPFS/NTFS
/dev/sda3            5664       19457   110800305    5  Extended
/dev/sda5            5664        9310    29294496   83  Linux
/dev/sda6            9311       14173    39062016   83  Linux
/dev/sda7           14174       19036    39062016    b  W95 FAT32
/dev/sda8           19037       19279     1951866   82  Linux swap / Solaris
/dev/sda9   *       19280       19457     1429753+  83  Linux

```

---

### Post by vanadium on 2009-03-23
It *is* mounted. Navigate, using nautilus file manager, to /windows (select "File system" under Places, then double-click the "windows" folder. Bookmark - Add bookmark (Ctrl+D) will add it to "Places".

---

### Post by maurolust on 2009-03-24
Solved! Thank you all.

---

