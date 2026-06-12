---
title: "A serious mounting problem [Resolved]"
date: 2007-02-25
forum: Hardware &amp; Laptops
---

### Post by palmbook on 2007-02-25
Hello,

I'm a very new user to Ubuntu (and Linux), even though I have been acquainted with Windows for nearly a decade. I installed Ubuntu on my computer on last Friday with a CD image provided in this site. Everything went well.

However, yesterday, I created a new partition upon my unpartitioned space and made it FAT32. I reboot into Ubuntu and could not see the drive.

My sudo fdisk -l and a dmesg command showed me that the drive was actually recognized to the system (/dev/sda6). So, I figured I should have tried to mount the drive.

I tried several approaches. None of them worked. The last thing I tried was to insert a line into /etc/fstab. I could not remember exactly what I wrote, but probably something like

> /dev/hda1   /media/windows  vfat  noauto,users,rw,exec   1  0

Then, I reboot my computer. Everything got worse from that point. I couldn't see anything! but CDROM drive and File System. Everything worked fine though. I could log-in, lauch applications, surf the net, etc. But my two other drives (a windows drive/NTFS and its own drive/SDA1) disappeared without a trace.

I removed the line from fstab. But nothing got better.

Did I do something terribly wrong? Please anyone guide me out of this problem.

Thank you very much.

---

### Post by palmbook on 2007-02-25
No one :confused:

---

### Post by aysiu on 2007-02-25
Please post the output of these commands: ```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by palmbook on 2007-02-25
> **aysiu said:**
> Please post the output of these commands: ```
sudo fdisk -l
cat /etc/fstab
df -h
```

Thank you very much. Here are the results.

fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5750    46186843+   7  HPFS/NTFS
/dev/sda2            5751        6633     7092697+  83  Linux
/dev/sda3            6634        7270     5116702+   f  W95 Ext'd (LBA)
/dev/sda4            7271        7296      208845   88  Linux plaintext
/dev/sda5            6634        6763     1044193+  82  Linux swap / Solaris
/dev/sda6            6764        7270     4072446    b  W95 FAT32


cat /etc/fstab

/dev/hda2            /                    ext2       defaults              1 1
proc                 /proc                proc       defaults              0 0



df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             6.7G  4.2G  2.2G  67% /
varrun                506M   92K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb             10M  136K  9.9M   2% /proc/bus/usb
udev                   10M  136K  9.9M   2% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   18M  489M   4% /lib/modules/2.6.17-11-generic/volatile
/dev/scd0             481M  481M     0 100% /media/dvdrecorder

---

### Post by aysiu on 2007-02-25
Paste these commands into the terminal, in this order: ```
sudo mkdir /windows1
sudo mkdir /windows2
sudo cp /etc/fstab /etc/fstab.backup
sudo nano /etc/fstab
``` This last command will open up the /etc/fstab file for editing. Paste in these two lines: ```
/dev/sda1 /windows1 ntfs nls=utf8,umask=0222 0 0
/dev/sda6 /windows2 vfat iocharset=utf8,umask=000 0 0
``` Then save (Control-X, Y, Enter) and finally ```
sudo mount -a
``` Afterwards, the NTFS partition should be mounted in the /windows1 directory. The FAT32 partition should be mounted in the /windows2 directory.

---

### Post by palmbook on 2007-02-25
Thank you very much for your kindness. I really appreciate your help.

I did the steps you mentioned. df -h showed me that my drives were mounted.

> charles@charles-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             6.7G  4.2G  2.2G  67% /
varrun                506M   92K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb             10M  136K  9.9M   2% /proc/bus/usb
udev                   10M  136K  9.9M   2% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   18M  489M   4% /lib/modules/2.6.17-11-generic/volatile
/dev/sda1              45G   26G   19G  59% /windows1
/dev/sda6             3.9G  2.0K  3.9G   1% /windows2
/dev/scd0             481M  481M     0 100% /media/dvdrecorder


I can also access the files from windows1 and windows 2 folders.

However, The only things I can see when I go to "Places > Computer" are FileSystem drive and my DVD drive. Is there anyway to fix this (my windows drive used to be there before)? Also, do I need to mount my sda2 (or sda0?) to also get my Linux drive (the one that's not FileSystem)?

---

### Post by aysiu on 2007-02-25
Yes. Go to /windows1 and bookmark it in the file manager. Then do the same for /windows2. Then both will show up in Places.

This may help you with the Linux drive:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by palmbook on 2007-02-26
Thank you a lot. You saved my (Linux) life!

Your contribution really encouraged my on keeping using Ubuntu :)

---

### Post by aysiu on 2007-02-26
Great to hear.

---

