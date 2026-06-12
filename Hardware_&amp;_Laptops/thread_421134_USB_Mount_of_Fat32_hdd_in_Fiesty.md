---
title: "USB Mount of Fat32 hdd in Fiesty"
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by gotmonkey on 2007-04-24
I am trying to switch from Fedora to Ubuntu Feisty. I have a usb hdd (FAT32) that I transferred all of my stuff from my home directory in Fedora to migrate to Ubuntu. I booted my UFF system and when I connected my usb-hdd to the notebook, I received this error:

Cannot mount volume.
You are note privleged to mount this volume.

When I set up my usb-hdd, I set it up in fedora using qparted. created the file structure and formatted the drive in FAT32, then copied my files to it. I pulled the fedora hdd from my notebook, installed my ubuntu hdd, and tried to mount the usb-hdd. 

fdisk -l gives me this, so I know that the system is recognizing the drive

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161    b  W95 FAT32


Any Ideas?

----------
edit
----------
I was able to mount the drive using this:
sudo mount -t vfat /dev/sdb1 /media/usb80 -o umask=0222

I copied over my files to the folder that I wanted, then I had to run
sudo chmod -R 777 /path/to/folder
to unlock the permissions of the files.

Oddly enough, I cannot connect any of my usb flash drives as well. I get the same error

---

### Post by bwhite82 on 2007-04-24
Yes, it's a permissions problem. You need to edit your /etc/fstab to give yourself ownership to it.

---

### Post by gotmonkey on 2007-04-24
I think that I discovered part of the problem. I installed automatix2 to install some bit of code for me. I installed the automatix read/write ntfs and fat32 mounter. Once I removed it, I tried both of usb flash drives and my usb-hdd.  All three seemed to automount corrently.


Has anyone had similar issues with the automatix installer?

---

### Post by bwhite82 on 2007-04-24
I keep saying it, stay   away   from   automatix.

---

### Post by gotmonkey on 2007-04-24
> **Soldierboy said:**
> I keep saying it, stay   away   from   automatix.

is there a problem with it? other than the one I just experienced

---

