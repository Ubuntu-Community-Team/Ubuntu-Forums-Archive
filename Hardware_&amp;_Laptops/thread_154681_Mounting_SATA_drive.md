---
title: "Mounting SATA drive"
date: 2006-04-03
forum: Hardware &amp; Laptops
---

### Post by nebc on 2006-04-03
I know there are threads on this but so far they have not completly done the trick.

I have a dual boot currently configured across 2 SATA drives.  One 160GB hard drive is home to Ubuntu (/dev/sdb) where the other hardrive has a 80GB ntfs partition for windows and an 80GB vfat partition that I would like both ubuntu and windows to see.

This is the contents of /etc/fstab:

/dev/sdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda2       /media/sda2     vfat    auto,rw,user 0 0
/dev/sdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

I added the /dev/sda2 line and I'm pretty darn sure that it is the correct partition.  However, after rebooting I cannot get access to it.  When I ls media I get:

cdrom/   cdrom0/  cdrom1/  floppy/  floppy0/

Suspiciously I only have 2 CD drives (1 is DVD I suppose).  At any suggestions?  If you need more information just ask and I will happily provide.

Cheers.

---

### Post by Princey on 2006-04-03
[QUOTE=nebc]I know there are threads on this but so far they have not completly done the trick.

I have a dual boot currently configured across 2 SATA drives.  One 160GB hard drive is home to Ubuntu (/dev/sdb) where the other hardrive has a 80GB ntfs partition for windows and an 80GB vfat partition that I would like both ubuntu and windows to see.

This is the contents of /etc/fstab:

/dev/sdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda2       /media/sda2     vfat    auto,rw,user 0 0
/dev/sdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

I added the /dev/sda2 line and I'm pretty darn sure that it is the correct partition.  However, after rebooting I cannot get access to it.  When I ls media I get:

cdrom/   cdrom0/  cdrom1/  floppy/  floppy0/

Suspiciously I only have 2 CD drives (1 is DVD I suppose).  At any suggestions?  If you need more information just ask and I will happily provide.

Cheers.[/QUOTE]

Somehow I've noticed you're trying to mount the fat32 partition within the assigned mount point for reference by root. Here's what I'd advice.

1. In the terminal type this > sudo mkdir FATDRIVE (of course, you can substitute "FATDRIVE" with any name of your choice.

2. Type the following at the promt when you're done: > sudo gedit /etc/fstab and replace the entry that you have > /dev/sda2       /media/sda2     vfat    auto,rw,user 0 0 with > /dev/sda2       /home/username/FATDRIVE     vfat    auto,rw,user 0 0 Remember to use the name of the directory that you created and replace username with your username that you created setting up your machine.

3. Click save in gedit and close it. Type the following command at the terminal > sudo umount /media/sda2 press enter then follow with this command > sudo mount -a press enter and close. Your drive should now show up as a folder in your home directory. Let me know if anything goes wrong.

---

### Post by nebc on 2006-04-03
Thanks so much!

---

### Post by Princey on 2006-04-03
[QUOTE=nebc]Thanks so much![/QUOTE]


You're welcome:cool:

---

