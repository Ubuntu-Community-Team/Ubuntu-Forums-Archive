---
title: "&quot;Permission denied&quot; copying file"
date: 2005-11-07
forum: General Help
---

### Post by actinic on 2005-11-07
keywords: permission denied FAT32 NFS fstab

Hi folks here's the error message when trying to copy a file from
pc #1 'Abit' to pc #2 'Albatron' over the network containing a mounted FAT32 partition ...

```
  
root@abit:/home/ftp# cp tu1.avi /home/ftpdown/Albatron/
cp: cannot create regular file `/home/ftpdown/Albatron/tu1.avi': Permission denied
root@abit:/home/ftp#
```

Here's my fstab from the source 'Abit' computer housing the file
I want to move ...

```

arcturus@abit:~$ cat /etc/fstab
# /etc/fstab: filesystem table.
#
# filesystem  mountpoint  type  options  dump  pass
/dev/hda5  /  reiserfs  defaults  0  1

proc  /proc  proc  defaults  0  0
/dev/fd0  /floppy  vfat  defaults,user,noauto,showexec,umask=022  0  0
usbfs  /proc/bus/usb  usbfs  devmode=0666  0  0
sysfs  /sys  sysfs  defaults  0  0
tmpfs  /dev/shm  tmpfs defaults  0  0
/dev/cdrom /cdrom  iso9660  defaults,ro,users,noexec,noauto  0  0
/dev/dvd /dvd  iso9660  defaults,ro,users,noexec,noauto  0  0
/dev/cdaudio /cdaudio  iso9660  defaults,ro,users,noexec,noauto  0  0
/dev/hda1 /mnt/hda1 ntfs auto,users,exec,ro,umask=000 0 0
/dev/hda6 none swap defaults 0 0
192.168.0.2:/mnt/windows        /home/ftpdown/Albatron  nfs     rw,users        0 0
```

and here's the fstab for the target 'Albatron' pc I'm trying
to send the file to ...

```

arcturus@Albatron:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda6       /               reiserfs notail          0       1
/dev/sda1       /media/sda1     ntfs    defaults        0       0
/dev/sda5       /mnt/windows    vfat    iocharset=utf8,umask=000        0       0
/dev/sda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

finally, ...


```

root@Albatron:/home/arcturus# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2187    17567046    7  HPFS/NTFS
/dev/sda2            2188       19457   138721275    f  W95 Ext'd (LBA)
/dev/sda5            2188       16668   116318601    b  W95 FAT32
/dev/sda6   *       16669       19356    21591328+  83  Linux
/dev/sda7           19357       19457      811251   82  Linux swap / Solaris
```

Could someone kindly tell me why I'm getting this 'permission denied' error?  Thx.

---

### Post by nszabolcs on 2005-11-07
what are the permissions of the directory?
```

ls -l -d /home/ftpdown/Albatron/

```

---

### Post by actinic on 2005-11-07
[QUOTE=nszabolcs]what are the permissions of the directory?
```

ls -l -d /home/ftpdown/Albatron/

```[/QUOTE]
```

root@abit:~# ls -l -d /home/ftpdown/Albatron
drwxr-xr-x  12 root root 32768 Dec 31  1969 /home/ftpdown/Albatron
root@abit:~#
```

This directory is FAT32.

---

### Post by actinic on 2005-11-08
bump

---

### Post by Borusa on 2005-11-08
```

drwxr-xr-x  12 root root 32768 Dec 31  1969 /home/ftpdown/Albatron

```
Quick run through of what all this means...
the first character "d" indicates it's a directory.
The next three are the owner's permissions - the owner can (r)ead, (w)rite and e(x)ecute files within. The next three are the owning group's permissions. The group can (r)ead and e(x)ecute, but you'll see the (w)rite option is missing.
The last three are the "other" permissions, and you'll spot that you can't (w)rite either.

Next is the number of links to the directory, then the owner and the owning group.

You have three options :- 
1) Change the owner/group to include your user.
2) execute your copy command with sudo (bad in principle, probably undesirable)
3) change the permissions on the file.

To do the last of these, do ```
sudo chmod u+rwx /home/ftpdown/Albatron
```

---

### Post by actinic on 2005-11-08
> 
2) execute your copy command with sudo (bad in principle, probably undesirable)
the cp command was executed as root

> 3) change the permissions on the file

```

root@abit:/home/ftp# chmod u+rwx tu1.avi
root@abit:/home/ftp# cp tu1.avi /home/ftpdown/Albatron/
cp: cannot create regular file `/home/ftpdown/Albatron/tu1.avi': Permission denied
```

where,

-rwxrwxrwx  1 ftp ftp      3248128 Nov  6 21:33 tu1.avi

---

### Post by slux on 2005-11-10
NFS doesn't allow the root user of the client machine to access the server mount by default. You need to either change permissions for the mount (might be the preferred way) or add no_root_squash into your NFS mount options.

---

### Post by actinic on 2005-11-10
Thanks, I fooled around with different suggestions and in exasperation rebooted.  Guess what?  It works!  Problem is I don't quite know which suggestion(s) did the trick.

Must not have re-mounted properly after the changes.

It's mount -a, right?

---

### Post by Sukarn on 2006-06-04
**mount -a** mounts the unmounted partitions according to /etc/fstab

---

