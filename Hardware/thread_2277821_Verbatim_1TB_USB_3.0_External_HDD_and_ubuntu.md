---
title: "Verbatim 1TB USB 3.0 External HDD and ubuntu"
date: 2015-05-11
forum: Hardware
---

### Post by janeku2 on 2015-05-11
Hello,
I have Verbatim Store'n'Go HDD, size 1TB. It says it is FAT32 formatted (factory settings)
It used to be read under Ubuntu after clean installation and I perform some read=write actions (getting my backup files, size 500GB).
I copy some things to another Laptop (runs on Windows 7 but it wasn't mine) and after that I store it back to safe.
Today I decide to backup some other documents and when I tried to access it on Ubuntu 14.04.2 LTS (64bit) I couldn't. I hear some repetitorious clicks and nothing happens.
I tried it under Windows 7 and it opens normal.
Any one experienced such thing ?
Should I formatted in order to start work as it should or there is a Ubuntu problem-issue for this situation ?
Regards,

EDIT: When I type dmesg | tail -50 it says:
[ 1579.339902] usb 1-1: new high-speed USB device number 6 using ehci-pci
[ 1579.474975] usb 1-1: New USB device found, idVendor=18a5, idProduct=0237
[ 1579.474988] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1579.474995] usb 1-1: Product: Portable USB 3.0 Drive
[ 1579.475001] usb 1-1: Manufacturer: Verbatim
[ 1579.475006] usb 1-1: SerialNumber: 1410210021229133
[ 1579.475670] usb-storage 1-1:1.0: USB Mass Storage device detected
[ 1579.477278] scsi7 : usb-storage 1-1:1.0


Any suggestion ????

---

### Post by sudodus on 2015-05-12
Is the device recognized at all, when you run Ubuntu? Please post the output of the following command

```
sudo parted -l
```

(... space minus ell)

-o-

My general advice (without knowing more about it) would be to boot into Windows and use ***chkdsk*** to repair it (there may be errors, that stop Ubuntu from reading the FAT32 file system)

```
chkdsk /f X:
```

where X is the drive letter in Windows (maybe D: or E:, check in Windows).

---

### Post by janeku2 on 2015-05-12
Ok, just did parted -l and this is the result:

```
Model: ATA WDC WD1600AAJS-0 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  256MB  255MB  primary   ext2         boot
 2      257MB   160GB  160GB  extended
 5      257MB   160GB  160GB  logical                lvm


Model: ATA WDC WD5000AADS-0 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32,3kB  500GB  500GB  primary  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 158GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0,00B  158GB  158GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 2147MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0,00B  2147MB  2147MB  linux-swap(v1)

```

I did full format with Verbatim HDD utility. I checked on other computer running Ubuntu (32bit) and it works without problem.
Looks like there is a problem either with Ubuntu on my machine or with USB ports.
My USB Sticks are working with no problem on same USB ports.

Is there a way to check USB port settings and possible problem with groups that my account is assigned to ???
When I type groups I got:

petrika root adm dialout cdrom sudo dip plugdev lpadmin sambashare

dialout is a group for CHIRP to work proper with my HAM radio.

---

### Post by sudodus on 2015-05-13
> **janeku2 said:**
> ```
Model: ATA WDC WD1600AAJS-0 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  256MB  255MB  primary   ext2         boot
 2      257MB   160GB  160GB  extended
 5      257MB   160GB  160GB  logical                lvm

```
Western Digital disk sda
> 
```
Model: ATA WDC WD5000AADS-0 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32,3kB  500GB  500GB  primary  ext4

```
Western Digital disk sdb
> 
```
Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 158GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0,00B  158GB  158GB  ext4

```
^^^
lvm maps in sda
vvv
> 
```
Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 2147MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0,00B  2147MB  2147MB  linux-swap(v1)

```

I did full format with Verbatim HDD utility. I checked on other computer running Ubuntu (32bit) and it works without problem.
Looks like there is a problem either with Ubuntu on my machine or with USB ports.
My USB Sticks are working with no problem on same USB ports.

Is there a way to check USB port settings and possible problem with groups that my account is assigned to ???
When I type groups I got:

petrika root adm dialout cdrom sudo dip plugdev lpadmin sambashare

dialout is a group for CHIRP to work proper with my HAM radio.

No, the Verbatim drive is not found. Sometimes the hardware or firmware or drivers are not compatible with a device. USB hard disk drives will usually work, but not always. There are often problems with USB 3 (probably because it is a newer standard, and everything is not quite according to the standard specifications).

You could try another version of Ubuntu or some other linux distro. Try without installing, only to check if that/those systems can find the Verbatim drive.
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

You can also look in the BIOS/UEFI menu system, if the drive is found, or if it helps to change some setting.

---

### Post by janeku2 on 2015-05-13
Strange thing is that IT WORKED when I installed 64bit version because I return back all backup i had on it to a new installation.
Then I back up some pictures from my friend, and after 2 weeks I uploaded to his laptop (running Windows 7, not registered, black background) these pictures. Then I left it back on place and after organizing my backup on my PC I decided to put it back on external disk. And then it happened.
I 'll try with Ubuntu live (the same that is installed on my PC) on my Lap top to see if there will be problem also. I hace 1 USB 3.0 port and 2 USB 2.0 ports so I could check if everything is fine. I'll also run Live Ubuntu on my PC to see if it is also running good.
So results will be posted here.
Regards

---

### Post by janeku2 on 2015-05-13
Looks like I found the cause of this problem. USB extension cable is the main problem maker that makes external hard disk not to be recognized. I put second extension cable to my PC and on the first I boot Live Ubuntu flash. On second (new one usb extension cable) and it was found in a moment :)
Then I reboot to normal and tried also with new USB cable and it worked without problem. Tried old one, the problem exists.
Looks like something happened with extension cable because previous it worked 100%. 
Interesting is that USB flash drives are working without a problem but HDD not. Looks like it can't stand such power from external HDD with these new combined USB+Micro connectors.
So I let the new cable also connected to my PC. I'll use old one for my flash disks. It is sad that my kids destroyed my front usb connector long time ago :( so I had to work from back ports.
Any way, thank you for your cooperation and I hope this situation will help to somebody else facing same problem :)
If everything did not worked I was going to ask you how to re-install USB drivers (if possible) if needed :)
Regards,

---

### Post by sudodus on 2015-05-14
I'm glad you found the problem and welcome back whenever you get another problem with Ubuntu :-)

---

