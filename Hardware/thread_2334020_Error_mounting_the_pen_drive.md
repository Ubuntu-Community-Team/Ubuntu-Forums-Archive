---
title: "Error mounting the pen drive"
date: 2016-08-15
forum: Hardware
---

### Post by sed_faster on 2016-08-15
Hello everyone,

I formatted the drive usb through gparted as ext4. After I finished formated the pen drive I can accessed than and copy files to inside her. But when I unplugged and plug the pen drive I received a prompt with this message:
```

Error mounting /dev/sdb1 at /media/eno/28mb: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdb1" "/media/eno/28mb"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.

```

What can I do to fix this?

My system is: Lubuntu 16.04LTS 64 bits

Thanks

---

### Post by ajgreeny on 2016-08-15
Before you unplugged the drive did you first unmount it or eject it properly?

If not the filesystem on it may be corrupt.

Plug it in and immediately run command ```
dmesg | tail -n 20
``` and post the output back here.
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by sed_faster on 2016-08-15
Didn't the first time I have this problem, but I unplugged the drive with out unmount or eject convenient. 

The ouput are:
```

[21718.834875] usb 2-1.1: new high-speed USB device number 8 using ehci-pci
[21718.927607] usb 2-1.1: New USB device found, idVendor=0457, idProduct=0151
[21718.927612] usb 2-1.1: New USB device strings: Mfr=0, Product=2, SerialNumber=3
[21718.927614] usb 2-1.1: Product: USB Mass Storage Device
[21718.927616] usb 2-1.1: SerialNumber: 6614f752e377c6
[21718.927995] usb-storage 2-1.1:1.0: USB Mass Storage device detected
[21718.928949] usb-storage 2-1.1:1.0: Quirks match for vid 0457 pid 0151: 80
[21718.928981] scsi host9: usb-storage 2-1.1:1.0
[21719.928493] scsi 9:0:0:0: Direct-Access     USB 2.0  Flash Disk       0.00 PQ: 0 ANSI: 2
[21719.929022] sd 9:0:0:0: Attached scsi generic sg2 type 0
[21719.929777] sd 9:0:0:0: [sdb] 54272 512-byte logical blocks: (27.8 MB/26.5 MiB)
[21719.930526] sd 9:0:0:0: [sdb] Write Protect is off
[21719.930534] sd 9:0:0:0: [sdb] Mode Sense: 00 00 00 00
[21719.931496] sd 9:0:0:0: [sdb] Asking for cache data failed
[21719.931502] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[21720.002988]  sdb: sdb1
[21720.006264] sd 9:0:0:0: [sdb] Attached SCSI removable disk
[21720.361551] JBD2: no valid journal superblock found
[21720.361561] EXT4-fs (sdb1): error loading journal

```

Thanks

---

### Post by ajgreeny on 2016-08-16
```
[21720.361551] JBD2: no valid journal superblock found
[21720.361561] EXT4-fs (sdb1): error loading journal
```
There is the problem; you damaged the filesystem on the disk by unplugging it without unmounting first.
You may be able to repair the file system on the USB by inserting it and making sure that it is not mounted running ```
sudo e2fsck -p /dev/sdb1
``` to see what output you get.

You must **NEVER** remove a USB disk without either unmounting it or ejecting it, most often from a right click on its icon in the file-manager or on the desktop.

This is just the same as in Windows, though I am aware that many people do not do this and simply pull out USBs without first using the Windows "Remove safely" utility.
Definitely not advisable!

---

### Post by sed_faster on 2016-08-16
Hello,

The output the command:
```

sudo e2fsck -p /dev/sdb1
28mb: Superblock has an invalid journal (inode 8).
CLEARED.
*** ext3 journal has been deleted - filesystem is now ext2 only ***

28mb: Superblock has_journal flag is clear, but a journal is present.
CLEARED.
28mb: Journal inode is not in use, but contains data.  CLEARED.
28mb: Recreate journal.
Creating journal (1024 blocks):  Done.

*** journal has been re-created - filesystem is now ext3 again ***
28mb: 14/6400 files (0.0% non-contiguous), 2165/25600 blocks
eno@enonet:~$ sudo e2fsck -p /dev/sdb1
28mb: Superblock has an invalid journal (inode 8).
CLEARED.
*** ext3 journal has been deleted - filesystem is now ext2 only ***

28mb: Superblock has_journal flag is clear, but a journal is present.
CLEARED.
28mb: Journal inode is not in use, but contains data.  CLEARED.
28mb: Recreate journal.
Creating journal (1024 blocks):  Done.

*** journal has been re-created - filesystem is now ext3 again ***
28mb: 11/6400 files (0.0% non-contiguous), 2150/25600 blocks

```

Buy, after I remove usb disk, after used the option unplugged with the security I receive the same message when I plugged the usb disk:
```

Error mounting /dev/sdb1 at /media/eno/28mb: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdb1" "/media/eno/28mb"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,        missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.

```

I formated again the usb disk, through gparted, as ext4, but the behavior is the same!
What do you suggest to resolve this problem?
Thanks for your advices and help.

---

### Post by ajgreeny on 2016-08-16
Hmmm! Not sure about this but it may be worth using gparted again to create a new partition table and then a new partition formated to whatever filesystem you want to see if that helps make the drive usable again.

If that is still no go then I'm afraid the drive is probably dead.

---

