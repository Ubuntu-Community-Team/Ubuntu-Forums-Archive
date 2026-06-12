---
title: "HowTo fix a corrupted usb flash drive"
date: 2016-08-24
forum: Hardware
---

### Post by ahmed.elrmady on 2016-08-24
hey guys! 
my usb flash drive has been corrupted  and i really need it to work , i get this message whenever i plug it into my pc 
 
[B]"Error mounting /dev/sdg1 at /media/gray/KINGSTON: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000" "/dev/sdg1" "/media/gray/KINGSTON"' exited with non-zero exit status 13: Corrupted file $UpCase
Failed to mount '/dev/sdg1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details."[/B]


anyway i could fix it !!!
plz help

---

### Post by ajgreeny on 2016-08-24
If this has an NTFS filesystem, have you removed it correctly from Windows previously, or did you perhaps just pull it out without using Window's own "safe removal" utility?

It is also possible, of course, that the flash drive is dead; they have a limited life and I have had such drives die on me before now.

Have you tried using **chkdsk** from Windows as suggested in the error, or do you not use Windows any more?

---

### Post by ahmed.elrmady on 2016-08-24
> **ajgreeny said:**
> If this has an NTFS filesystem, have you removed it correctly from Windows previously, or did you perhaps just pull it out without using Window's own "safe removal" utility?

It is also possible, of course, that the flash drive is dead; they have a limited life and I have had such drives die on me before now.

Have you tried using **chkdsk** from Windows as suggested in the error, or do you not use Windows any more?


i'm using ubuntu now yes ,so is there anyway i can get it work again !! :/

---

### Post by sudodus on 2016-08-24
1. It is best to use Microsoft tools to repair Microsoft file systems. Try to borrow a computer with chkdsk in Windows!

2. You can try to make a cloned copy of the drive, and try with some tools on the cloned copy: Testdisk and PhotoRec.
Testdisk might be able to restore the NTFS file system, but it might also damage it even more.
PhotoRec might be able to save at least some of the files, that are stored in the drive, even without a file system.

3. If that is not possible, or if it does not work to repair it with chkdsk, you might be able to create a new partition table and file system. But that would destroy the files that are stored in the drive.

See this link for more details: [Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

---

### Post by cwmoser on 2016-08-24
sudo  fsck  -t  vfat  /dev/sdi1

where /dev/sdi1 is the partition on your thumb drive.

---

### Post by yancek on 2016-08-24
You can try running "ntfsfix" as root user on the specific partition (sdg1) but the likelihood of that working is extremely unlikely.  ntfsfix will only repair minor problems.  
You have either not properly unmounted or removed the device or left the windows system hibernated while you had the device plugged in and those are just two of the more common possibilities.
If you are using an nitfs filesystem, you should have a windows installation.  If you dont have windows, why use ntfs?

As suggested above, use a windows operating system with that usb drive attached or some other windows tool.
Do you have windows installed?  Do you have another computer with windows?  Do you have a windows installation DVD which should have a repair option. 
This is not something that a Linux/Ubuntu system would be likely to solve because it is a proprietary filesystem.
Have you tried a windows forum or the microsoft support site?

---

### Post by ahmed.elrmady on 2016-08-24
ok thnx guys i'll try to check it on a windows machine and i hope it works

---

