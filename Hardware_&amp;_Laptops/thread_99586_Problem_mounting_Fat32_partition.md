---
title: "Problem mounting Fat32 partition"
date: 2005-12-05
forum: Hardware &amp; Laptops
---

### Post by Zooropa on 2005-12-05
I have a dual boot on the go here with windows XP and Ubuntu.

here is my fdisk:

zooropa@cpc2-kirk1-5-0-cust112:~$ sudo fdisk -l
Password:

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         255     2048256   1b  Hidden W95 FAT32
/dev/hda2             256        4079    30716280    7  HPFS/NTFS
/dev/hda3            4080        4141      498015   82  Linux swap / Solaris
/dev/hda4            4142       14593    83955690    5  Extended
/dev/hda5            4142        6573    19535008+   b  W95 FAT32
/dev/hda6   *        6574       14593    64420618+  83  Linux
zooropa@cpc2-kirk1-5-0-cust112:~$ sudo mount /dev/hda5 /media/windows -t vfat -o unmask=000
zooropa@cpc2-kirk1-5-0-cust112:~$


Can anyone help?
I'm trying to mount HDA5 so I can share files with XP, but I'm having absolutely no luck.
I'm told that hda5 should appear, but it isn't.

I was using this as a guide:
[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

---

### Post by Zooropa on 2005-12-05
A bit more info - 
when I go into XP, and create a text file, place it in "F:", the partition, I come back into Ubuntu and the file is there when I go to
File System > WIndows

I can't however save anything into that folder :S

I'm really new to this, sorry!

---

### Post by syncme on 2005-12-05
See if this works.

Try this:

sudo mkdir /media/windows98
sudo mount /dev/hda5 /media/windows98/ -t vfat -o iocharset=utf8,umask=000

Please let me know.

Syncme

---

### Post by Zooropa on 2005-12-05
Just done all that, and I still only see hda1, hda2, and a DVD I have in the drive on the desktop :S

zooropa@cpc2-kirk1-5-0-cust112:~$ sudo mkdir /media/windows98
Password:
zooropa@cpc2-kirk1-5-0-cust112:~$ sudo mount /dev/hda5 /media/windows98/ -t vfat -o iocharset=utf8,unmask=000
zooropa@cpc2-kirk1-5-0-cust112:~$

---

### Post by Zooropa on 2005-12-05
Further development?

zooropa@cpc2-kirk1-5-0-cust112:~$ sudo mount /dev/hda5 /windows/ -t vfat -o unmask=000
mount: /dev/hda5 already mounted or /windows/ busy
mount: according to mtab, /dev/hda5 is mounted on /windows
zooropa@cpc2-kirk1-5-0-cust112:~$
zooropa@cpc2-kirk1-5-0-cust112:~$


I noticed the drive seemed to run out of /windows/ and not /media/windows/

---

### Post by syncme on 2005-12-05
Once it's mounted in "/media/windows98" can you see anything by actually going to it via the console?

ls /media/windows98

Syncme

---

### Post by aysiu on 2005-12-05
Try this:
```
sudo umount /dev/hda5
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
``` Replace any line with /dev/hda5 in it with this line: ```
/dev/hda5  /windows  vfat   umask=000   0   0
``` Then save (Control-X), confirm (y), and exit (Enter). ```
sudo mount -a
``` Your partition should be in the /windows directory.

---

### Post by Zooropa on 2005-12-06
I'll give that a shot, thanks

---

### Post by Zooropa on 2005-12-06
That seemed to work in that i can now put files from ubuntu into the folder.

It's not on the desktop, but it's an improvement.

Thanks!

---

### Post by silex on 2005-12-07
[QUOTE=Zooropa]It's not on the desktop, but it's an improvement.[/QUOTE]

If you would like it to show up on the desktop, make a folder like /media/windows and change the /windows in the second block of code of aysiu's last post to /media/windows

When you make folders in /media and mount drives to them, Gnome will put it on the desktop.

---

### Post by aysiu on 2005-12-07
[QUOTE=Zooropa]
It's not on the desktop, but it's an improvement.[/QUOTE] Maybe this isn't the most sophisticated way to do it, but you can middle-click-drag /windows on to your desktop and select "link here."

---

