---
title: "maxtor external usb hard drive not being recognized"
date: 2008-02-27
forum: Hardware &amp; Laptops
---

### Post by davesec on 2008-02-27
hi,

i backed up a bunch of stuff from windows xp and then installed ubuntu. accidently deleted windows partitioning the harddrive, but that's another story. anyway now i want to import the stuff on this external hard drive to ubuntu but nothing happens when i plug it in. the device managed seems to show a 'mass storage device' but aside from that i've got nothing.

i've been told it's possible that if the drive is formatted as ntfs, then i'll have some issues? i can't format the drive because all my backup stuff is on it. is there anyway i can read the files?

thanks!
dave

---

### Post by Yellow Pasque on 2008-02-28
Plug the drive in. Now run these command and paste the output:
```
sudo lshw -businfo -C disk
fdisk -l
```

---

### Post by davesec on 2008-02-28
here's the result:

Bus info          Device      Class          Description
========================================================
scsi@0:0.0.0      /dev/sda    disk           55GB TOSHIBA MK6025GA
scsi@1:0.0.0      /dev/cdrom  disk           DVD-RAM UJ-831S
scsi@3:0.0.0      /dev/sdb    disk           232GB Basics Desktop


i also installed ntfs configuration tool, which is suppose to put an icon on my desktop that i can click on to browse the hard drive, but it's not working. hope this helps a bit!

---

### Post by davesec on 2008-02-28
whoops - and sudo fdisk -l:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x881e3473

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217        1277      489982+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7e227b14

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        6375    51199155    f  W95 Ext'd (LBA)
/dev/sdb2            6376       19123   102398310    7  HPFS/NTFS
/dev/sdb3           19124       30401    90590535    7  HPFS/NTFS
/dev/sdb5               2        6375    51199123+   7  HPFS/NTFS


thanks! the ext hard drive is partitioned into 3 separate drives, if that helps any.

---

### Post by Yellow Pasque on 2008-02-28
Ok. What version of Ubuntu are you using? If 7.10, I believe read/write support is built-in by default. Let's try this:

```
sudo apt-get install ntfs-3g
cd /media
sudo mkdir disk1
sudo mkdir disk2
sudo mkdir disk3
sudo chmod 777 *
sudo mount -t ntfs-3g -o rw,auto,user,exec,uid=1000 /dev/sdb2 /media/disk1
sudo mount -t ntfs-3g -o rw,auto,user,exec,uid=1000 /dev/sdb3 /media/disk2
sudo mount -t ntfs-3g -o rw,auto,user,exec,uid=1000 /dev/sdb5 /media/disk3

```

---

### Post by davesec on 2008-02-28
hit this error message:

dave@dave:~$ sudo apt-get install ntfs-3g
[sudo] password for dave:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ntfs-3g is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dave@dave:~$ cd /media
dave@dave:/media$ sudo mkdir disk1
dave@dave:/media$ sudo mkdir disk2
dave@dave:/media$ sudo mkdir disk3
dave@dave:/media$ sudo chmod 777 *
dave@dave:/media$ sudo mount -t ntfs-3g -o rw,auto,user,exec,uid=1000 /dev/sdb2 /media/disk1
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb2 /media/disk1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb2 /media/disk1 ntfs-3g defaults,force 0 0
dave@dave:/media$ 


i don't think i still have windows on this machine, i've been told i wrecked it when installing ubuntu. i also don't want to do anything that'll risk losing the information on this external harddrive; i'd much rather wait until i can bring the ext drive to a computer with windows and make additional backups of the stuff.

---

### Post by davesec on 2008-02-28
oh, and i am using 7.10!

---

### Post by Yellow Pasque on 2008-02-28
You probably wouldn't lose the data, but better safe than sorry. Ah, yes, NTFS, or as we called it when I worked at Sun Microsystems, **N**ice **T**ry **F**ile**S**ystem.
Just when you thought you had all of MS's shackles off...

---

### Post by davesec on 2008-02-29
just wanted to say i shut the drive down 'properly' in windows and all works well now.

thanks!

---

### Post by Yellow Pasque on 2008-02-29
> **davesec said:**
> just wanted to say i shut the drive down 'properly' in windows and all works well now.

thanks!
Good to know, you're welcome.

---

