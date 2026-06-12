---
title: "fstab Error"
date: 2014-05-03
forum: Hardware
---

### Post by Quarkrad on 2014-05-03
I've just recently installed 14.04 via a fresh install and get this message:   **The disk drive for /windows is not ready yet or present. Continue to wait or press S to to skip mounting ... etc.**  The only windows partition I have is sdb1 UUID=90F846A6F8468B04 - I press S to skip mounting but when I launch File Manager the partition is shown as mounted.  My fstab is: 
[B]
#Entry for /dev/sdb5 :
UUID=b5824ced-b7fb-4530-9e16-70c22fc46e77	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sdb6 :
UUID=bfd543ac-8ef8-4796-bff6-63c024b2f416	/home	ext4	defaults	0	2
/dev/sda1	/media/backup	ntfs-3g	defaults,locale=en_GB.UTF-8	0	0
#Entry for /dev/sdb1 :
UUID=90F846A6F8468B04	/media/sdb1	ntfs-3g	defaults,locale=en_GB.UTF-8	0	0
#Entry for /dev/sdb7 :
UUID=2B7BF9653C082084	/media/store	ntfs-3g	defaults,locale=en_GB.UTF-8	0	0
UUID=1A05-950C	/windows	vfat	utf8,umask=007,gid=46	0	1
#Entry for /dev/sdb8 :
UUID=42173f4c-cfd4-461b-a9c1-a1f0bdb52c64	none	swap	sw	0	0
[/B]
Many thanks.

---

### Post by SeijiSensei on 2014-05-03
Do you, or did you, have a USB device connected when installing?  /dev/sdb1 is already being mounted as /media/sdb1. /windows is/was on another device, one formatted as FAT32.

Perhaps you installed Linux using a USB pendrive?  If it was in the machine when /etc/fstab was created, it would be listed there.

---

### Post by Quarkrad on 2014-05-03
I did install ubuntu via a pen drive but windows was already installed in the HD.  According to gparted windows is on sdb1 and ubuntu on sdb 5 and sdb 6 (/ and /home).

---

### Post by SeijiSensei on 2014-05-03
I don't know what gparted thinks, but /etc/fstab is mounting this device as /windows
```
UUID=1A05-950C /windows vfat utf8,umask=007,gid=46 0 1
```
and mounting /dev/sdb1 as /media/sdb1
```
#Entry for /dev/sdb1 :
UUID=90F846A6F8468B04 /media/sdb1 ntfs-3g defaults,locale=en_GB.UTF-8 0 0
```

If you want to mount /dev/sdb1 to /windows, edit that entry accordingly and remove the other entry for /windows.  I'm guessing you no longer have the USB device inserted into the machine, but /etc/fstab wants to mount it, which gives you the error at boot.

---

### Post by oldfred on 2014-05-03
So what is this entry in fstab?

UUID=1A05-950C	/windows	vfat	utf8,umask=007,gid=46	0	1

Post this:
       sudo blkid -c /dev/null -o list

If UUID now does not exist comment it out with a # like other comments in fstab.

---

### Post by Quarkrad on 2014-05-04
That did it thank you - I compared the output of your command against fstab and put a # to comment out the line in question.

---

