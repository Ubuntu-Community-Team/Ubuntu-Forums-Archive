---
title: "Gutsy, Hard Drive Won't Mount"
date: 2007-10-25
forum: Hardware &amp; Laptops
---

### Post by jatoskep on 2007-10-25
I just installed Ubuntu Gutsy Gibbon on my computer, and used the whole hard drive. Before I did this I backed up all of my files on a 250GB MyBook external hard drive, but no matter what the hell I do I can not get it to mount. I have tried ntfs-3g and everything else I have found online about it but it won't mount. Any ideas? :confused:

---

### Post by taurus on 2007-10-25
Plug in that external harddrive.  Then, open a terminal and post the output of this command.

```
sudo fdisk -l
```
That would be lower case letter l, not number 1.

---

### Post by jatoskep on 2007-10-25
Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c74ae42

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

---

### Post by taurus on 2007-10-25
Try 

```
sudo mkdir /media/sdb1 
sudo mount -t ntfs /dev/sdb1 /media/sdb1
df -h
```

---

### Post by jatoskep on 2007-10-25
Hmm, it gave me this.

mkdir: cannot create directory `/media/sdb1': File exists
jatoskep@Jatoskep-Dell:~$ sudo mount -t ntfs /dev/sdb1 /media/sdb1
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/sdb1 ntfs-3g defaults,force 0 0



Should I try what it says? :\

---

### Post by jatoskep on 2007-10-25
*bump*

---

### Post by henklaak on 2007-10-25
It looks like something I experienced: 
If you do not properly shutdown windows, e.g. blue screens or just plain lockup, the NTFS partition stays marked as "in use". Go back to boot windows, do a clean shutdown, and it will probably mount in linux after that.

Regards, Henk.

---

### Post by jatoskep on 2007-10-25
> **henklaak said:**
> It looks like something I experienced: 
If you do not properly shutdown windows, e.g. blue screens or just plain lockup, the NTFS partition stays marked as "in use". Go back to boot windows, do a clean shutdown, and it will probably mount in linux after that.

Regards, Henk.

I completely removed windows. Will it work if I do this on another computer?

---

### Post by henklaak on 2007-10-26
I'd suggest to hook it up to another MS computer once, see if that works and do a 'safe hardware removal' (icon in the bottom right).
Gr. Henk.

---

