---
title: "External Hard Drive Improperly Removed?"
date: 2009-01-24
forum: Hardware
---

### Post by Jimmy Jazz on 2009-01-24
Hello,

I've been using a Lacie External Hard Drive with Ubuntu for a few months.  Recently, Ubuntu will not recognize the hard drive when I plug in the USB cable.  I just tested the Hard Drive with another laptop (running Vista), and it worked perfectly.

I remember one of the last times I used this hard drive in conjunction with my Ubuntu machine, I had some trouble disconnecting the hard drive properly.  The icon continued to appear on the desktop after I unmounted it (or thought I unmounted it).  I have a feeling that there is some flag or setting that was tweaked and is not allowing Ubuntu to recognize the hard drive upon being connected.  I was hoping someone who knows the inner workings of Ubuntu could advise me on some potential commands to run or files to look at to try to diagnose what may have happened.  Thanks!

---

### Post by taurus on 2009-01-24
Plug the harddrive in.  Then, open a terminal and post the outputs of these commands here.

Applications -> Accessories -> Terminal
```
dmesg | tail
sudo fdisk -l
df -h
```

---

### Post by Jimmy Jazz on 2009-01-24
Hi, thank you for the reply.  Here are the results of those 3 commands:


flio@flio-laptop:~$ dmesg | tail
[14226.950518] usb 5-3: new high speed USB device using ehci_hcd and address 38
[14225.254029] usb 5-3: device descriptor read/64, error -71
[14225.470651] usb 5-3: device descriptor read/64, error -71
[14227.494624] usb 5-3: new high speed USB device using ehci_hcd and address 39
[14225.797150] usb 5-3: device descriptor read/64, error -71
[14226.012804] usb 5-3: device descriptor read/64, error -71
[14226.228469] usb 5-3: new high speed USB device using ehci_hcd and address 40
[14228.445137] usb 5-3: device not accepting address 40, error -71
[14228.555957] usb 5-3: new high speed USB device using ehci_hcd and address 41
[14228.963293] usb 5-3: device not accepting address 41, error -71

flio@flio-laptop:~$ sudo fdisk -l

Disk /dev/sda: 98.5 GB, 98522403840 bytes
255 heads, 63 sectors/track, 11978 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        2221    17800020    7  HPFS/NTFS
/dev/sda3           11372       11977     4867695   db  CP/M / CTOS / ...
/dev/sda4            2222       11371    73497375    5  Extended
/dev/sda5            2222       10997    70493188+  83  Linux
/dev/sda6           10998       11371     3004123+  82  Linux swap / Solaris

Partition table entries are not in disk order


flio@flio-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              67G   31G   33G  49% /
varrun                502M  108K  501M   1% /var/run
varlock               502M     0  502M   0% /var/lock
udev                  502M   64K  501M   1% /dev
devshm                502M  668K  501M   1% /dev/shm
lrm                   502M   39M  463M   8% /lib/modules/2.6.24-22-generic/volatile
gvfs-fuse-daemon       67G   31G   33G  49% /home/flio/.gvfs

---

### Post by taurus on 2009-01-24
Try running lsusb from a first and see if your USB drive shows up after that.  It could take a few seconds though before it does though.

```
lsusb
sudo fdisk -l
```

---

### Post by Bucky Ball on 2009-01-25
I am having a similar problem to this with a WD GreenPower 500Gb external USB/eSATA drive. Always worked fine on USB, tried it today on eSATA and didn't work, as usual, but now back on USB, nothing. Doesn't show in any of the command outputs from the post above:

```
dmesg | tail
sudo fdisk -l
df -h
lsusb

```I have also tried it with XP and fine. Closed it down and removed safely, so not that. Mind if I join in?? :)

---

### Post by cariboo on 2009-01-25
There seems to be a bug in hotplugging, the only way I can get my eSata drive to show up is to plug in a usb device first, or have it plugged in and turned on at boot.

Jim

---

### Post by Jimmy Jazz on 2009-01-25
Hmmm...my external drive is suddenly being recognized again.  This is before I saw the latest posts in this thread.  Very strange.  Taurus, thank you for the troubleshooting tips...I have a feeling the drive going to have similar behavior in the future, so I will keep the lsusb (and other posted commands) handy.

---

### Post by hexanol on 2009-01-26
> There seems to be a bug in hotplugging, the only way I can get my eSata drive to show up is to plug in a usb device first, or have it plugged in and turned on at boot.

Speaking for myself, I didn't had any problems hotplugging my external drive via eSata on Intrepid. In fact, I have seen this thread because I was looking for informations as if there was a special procedure to "shut down" the hard drive before unplugging it or no. Because when I turn the power on my HDD enclosure, a few seconds latter there's a new device listed in /dev (/dev/sdb in this case), but then, if I want to turn it off, well I was wondering if there was something special to do or if you just had to, well, turn it off.

I receive my enclosure today (it's a Thermaltake Blacx). I was happy to see that it worked fine in Ubuntu... but less happy when I saw that Vista wasn't able to handle hotplugging correctly. Crap.

---

### Post by Bucky Ball on 2009-01-28
Select the external drive, right click and 'unmount'.

---

