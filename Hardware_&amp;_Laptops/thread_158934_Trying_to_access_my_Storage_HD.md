---
title: "Trying to access my Storage HD"
date: 2006-04-12
forum: Hardware &amp; Laptops
---

### Post by Ali Baba on 2006-04-12
Alright, i have two HDs, a 40gb and a 160gb. 40gb used to have windows, and the 160gb is a storage drive, with all my videos and school work and stuff.

I just recently installed ubuntu on the 40gb. After setting up ubuntu, when i go to the "Places" Menu, i see "Computer" and "hdb1". I assume hdb1 is my 160gb drive. The problem is, when i click to access the files on the hdb1, it tells me:

"The folder contents could not be displayed. You do not have the permission necessary to view the contents of 'hdb1'."

I only have one user, and i should have all permissions, correct?

Also, when i go to System>Administration>Disks, i see my 160gb harddisk, but there, it gives me /dev/hdb , instead of hdb1. I am at a loss.

Can anyone assist me? I'm a noob at ubuntu.

Thanks in advance.

---

### Post by taurus on 2006-04-12
I guess your second harddrive is in NTFS and somehow, you mount it with only root can read from it!  Can you post the output of this command from a terminal.  To open a terminal in case you don't know how, click on Applications -> Accessories -> Terminal and type
```

more /etc/fstab

```

---

### Post by Ali Baba on 2006-04-12
[QUOTE=taurus]I guess your second harddrive is in NTFS and somehow, you mount it with only root can read from it!  Can you post the output of this command from a terminal.  To open a terminal in case you don't know how, click on Applications -> Accessories -> Terminal and type
```

more /etc/fstab

```[/QUOTE]

Alright i went to terminal and i typed that code.

The entire output it:

```
ismail@ubuntu:~$ more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb1       /media/hdb1     ntfs    defaults        0       0
/dev/hda1       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

What to do with that information?

---

### Post by aysiu on 2006-04-12
What filesystem is /dev/hdb1? Can you post the output of this command? ```
sudo fdisk -l
```

---

### Post by Ali Baba on 2006-04-12
[QUOTE=aysiu]What filesystem is /dev/hdb1? Can you post the output of this command? ```
sudo fdisk -l
```[/QUOTE]

The output:

```

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1          61      489951   82  Linux swap / Solaris
/dev/hda2              62        4998    39656452+  83  Linux

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       19457   156288321    7  HPFS/NTFS

```

---

### Post by aysiu on 2006-04-12
```
sudo umount /dev/hdb1
sudo mkdir /storage
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
``` If there's a line referring to /dev/hdb1, replace it with this one... if there's no line referring to it, just add this one... ```
/dev/hdb1 /storage ntfs nls=utf8,umask=0222 0 0
``` Save (control-x), confirm (y), and exit (Enter). ```
sudo mount -a
``` Go to /storage. If *sudo mount -a* doesn't remount it properly, try rebooting.

---

### Post by Ali Baba on 2006-04-12
[QUOTE=aysiu]```
sudo umount /dev/hdb1
sudo mkdir /storage
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
``` If there's a line referring to /dev/hdb1, replace it with this one... if there's no line referring to it, just add this one... ```
/dev/hdb1 /storage ntfs nls=utf8,umask=0222 0 0
``` Save (control-x), confirm (y), and exit (Enter). ```
sudo mount -a
``` Go to /storage. If *sudo mount -a* doesn't remount it properly, try rebooting.[/QUOTE]

Thank you very much, it worked. :)

---

### Post by mooon on 2006-04-13
Hi.

I tried to do the same and I think I did something very wrong because now I cannot find hdb5 anymore. The backup should be made but mayby you can help me out, because I very new.
Below are my actions:

meike99@53542106:~$ more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       /media/hdb5     ntfs    defaults
0       0
/dev/hdb7       /media/hdb7     ntfs    defaults        0       0
/dev/hdb8       /media/hdb8     ntfs    defaults        0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

meike99@53542106:~$ sudo fdisk -l
Password:

Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        2671    21454776   83  Linux
/dev/hdb2            2672       24792   177686932+   f  W95 Ext'd (LBA)
/dev/hdb5            2672       10302    61295976    7  HPFS/NTFS
/dev/hdb6   *       10303       13489    25599546   8e  Linux LVM
/dev/hdb7           13490       16709    25864618+   7  HPFS/NTFS
/dev/hdb8           16710       24792    64926666    7  HPFS/NTFS
meike99@53542106:~$ sudo umount /dev/hdb5
meike99@53542106:~$ sudo mkdir /storage
mkdir: cannot create directory `/storage': File exists
meike99@53542106:~$ sudo cp /etc/fstab /etc/fstab_backup
meike99@53542106:~$ sudo nano /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       /media          ntfs    nls=utf8, umask=0222 0   0
/dev/hdb7       /media/hdb7     ntfs    defaults        0       0
/dev/hdb8       /media/hdb8     ntfs    defaults        0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


meike99@53542106:~$ sudo mount -a
[mntent]: line 6 in /etc/fstab is bad
mount: mount point 0 does not exist
mount: wrong fs type, bad option, bad superblock on /dev/hdb8,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by aysiu on 2006-04-13
/dev/hdb5 is Linux LVM, but you have it in /etc/fstab as NTFS.

---

### Post by mooon on 2006-04-13
I changed /dev/hdb5 /media/hdb5 ntfs defaults
into /dev/hdb5 /media ntfs nls=utf8, umask=0222 0 0 well actually i changed media into storage because that went wrong the first time.
before it said the thing anout having no access, because ntfs i think now i can access but it is empty?

---

### Post by aysiu on 2006-04-13
[QUOTE=mooon]I changed /dev/hdb5 /media/hdb5 ntfs defaults
into /dev/hdb5 /media ntfs nls=utf8, umask=0222 0 0 well actually i changed media into storage because that went wrong the first time.
before it said the thing anout having no access, because ntfs i think now i can access but it is empty?[/QUOTE] Sorry. I misread your original post. I was looking at the LVM line, not the NTFS one.

Do this: ```
sudo umount /media/hdb5
sudo mkdir /ntfs_drive
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
``` Replace ```
/dev/hdb5 /media ntfs nls=utf8, umask=0222 0 0
``` with ```
/dev/hdb5 /ntfs_drive ntfs nls=utf8, umask=0222 0 0
``` Save (control-x), confirm (y), and exit (Enter) and then ```
sudo mount -a
``` Your partition will be mounted in a directory called /ntfs_drive.

---

### Post by mooon on 2006-04-14
Thanks, but now I went to the drive and it lists nothing in it, so it is empty?
meike99@53542106:~$ cd /ntfs_drive
meike99@53542106:/ntfs_drive$ ls -A
meike99@53542106:/ntfs_drive$
or is it the wrong command, sorry for the trouble.

---

### Post by aysiu on 2006-04-14
[QUOTE=mooon]Thanks, but now I went to the drive and it lists nothing in it, so it is empty?
meike99@53542106:~$ cd /ntfs_drive
meike99@53542106:/ntfs_drive$ ls -A
meike99@53542106:/ntfs_drive$
or is it the wrong command, sorry for the trouble.[/QUOTE] If you type ```
mount
``` or ```
df -h
``` you should see if it's mounted or not. If it's not mounted, try the ```
sudo mount -a
``` command. If that doesn't work, reboot.

After a reboot, if it still looks empty, it's probably empty.

---

