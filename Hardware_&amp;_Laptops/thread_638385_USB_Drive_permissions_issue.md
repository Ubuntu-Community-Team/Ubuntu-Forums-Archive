---
title: "USB Drive permissions issue"
date: 2007-12-12
forum: Hardware &amp; Laptops
---

### Post by EarthAndAllStars on 2007-12-12
My 2 GB USB drive is having permission issues on my machine, but not another ubuntu 7.10 strange...

I tried this:

[I]<alt>+F2
gksudo nautilus
Browse to "/media"
right click on the folder representing the USB Media in question
select "Permissions"
Adapt the permission for "Other" to your liking.[/I]

And it said I didn't have enough permissions to change the permissions! 

The strange this is that I can copy files from the terminal using sudo. 

Here is my fstab:

proc /proc proc defaults 0 0
# Entry for /dev/hda2 :
UUID=b35a6071-e0b6-499d-b0c6-f1f9f3e02a28 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda5 :
UUID=5e3aae2f-3f88-4e90-b8bb-216e81c5a7fa none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0
/dev/hdb1 /media/Drive\040D ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/hda1 /media/Drive\040C ntfs-3g defaults,locale=en_US.UTF-8 0 0

My mount point for the USB drive is /media/2GBUSB

I tried to reset the permission using sudo and chmod but they didn't take.

---

### Post by dravine on 2008-01-07
I am also having this problem, and I'm starting to get frustrated at the lack of effort that seems to be put in to fixing it.

Gutsy has been out for weeks, and this issue is STILL being reported by users. What the heck is going on in ubuntuland?

---

### Post by dravine on 2008-01-07
I found a fix for this (not sure if it will work for you)

Open 'gconf-editor' via alt-f2 or from the terminal

browse to /system/storage/default_options/vfat

the mount_options key had a umask of 077 on my machine, which is the cause of the problem
A value of 011 or 022 will make it work properly.

Cheers

- Jesse

---

