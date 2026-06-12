---
title: "[SOLVED] USB Hard Drive Error - Not Allowed to Write"
date: 2008-03-05
forum: Hardware &amp; Laptops
---

### Post by dicecca112 on 2008-03-05
I have a new USB Hard Drive connected via USB, I cannot write to the drive

here is some info
> 
Bus info          Device      Class       Description
=====================================================
scsi@0:0.0.0      /dev/cdrom  disk        DVD+-RW DR-K17Y
scsi@2:0.0.0      /dev/sda    disk        149GB ST9160823AS
scsi@8:0.0.0      /dev/sdb    disk        149GB 00BEVS-07RST0
dicecca@dicecca-laptop:~$ Drive is formated as ext3 and is sdb

Error is 
> 
Error while copying to "/media/disk".  You do not have permissions to write to this folder.

---

### Post by unutbu on 2008-03-05
Run
```

cat /etc/fstab | grep sdb

```

You should find something like
```

/dev/sdb       /media/disk   ext3   user,noauto,exec 0       0

```

Edit /etc/fstab so 'user' appears as one of the options.
Don't copy/paste the line I wrote; I just made it up. Instead take what you have and just add 'user' in the third space-separated string-clump from the right.

Then umount and mount again. Hope that works.

---

### Post by dicecca112 on 2008-03-05
didn't work, still gives the same error

---

### Post by taurus on 2008-03-05
Can you post the outputs of these commands?

```
sudo fdisk -l
df -h
id
```

---

### Post by dicecca112 on 2008-03-05
Per your request

> dicecca@dicecca-laptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d81f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9726    78124063+  83  Linux
/dev/sda2            9727        9969     1951897+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000441cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux
dicecca@dicecca-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              74G   14G   57G  20% /
varrun               1013M  128K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M  112K 1013M   1% /dev
devshm               1013M     0 1013M   0% /dev/shm
lrm                  1013M   24M  990M   3% /lib/modules/2.6.22-14-generic/volatile
/dev/sdb1             147G  189M  140G   1% /media/disk
dicecca@dicecca-laptop:~$ id
uid=1000(dicecca) gid=1000(dicecca) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),108(lpadmin),110(admin),115(netdev),117(powerdev),1000(dicecca)
dicecca@dicecca-laptop:~$ 


---

### Post by taurus on 2008-03-05
You can change the ownership of /media/disk from root to your login name, dicecca, so you can write to it anytime you want without using sudo/gksudo.

```
sudo chown -R dicecca:dicecca /media/disk
ls -la /media
```

---

### Post by dicecca112 on 2008-03-05
thank you taurus that did it.

---

