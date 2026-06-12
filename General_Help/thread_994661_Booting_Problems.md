---
title: "Booting Problems"
date: 2008-11-27
forum: General Help
---

### Post by AduNeButt on 2008-11-27
I recently decided that my virus-ridden Windows Vista running desktop is going to waste, so I decided to put a fresh install of Ubuntu on it.  Being a first time Linux user I'm not really too experienced with its installation, so here's my problem.

It seems my computer is still trying to boot into Vista, as here is the error I'm getting:

"Booting 'Windows Vista'

acpi
Vista Loader 2.1.2

Done!
fallback 1
find --set-root /bootmgr

Error 17: File not found
Booting 'Windows NT/2000/XP'

fallback 2
find --set-root /ntldr

Error 17: File not found
Booting 'Enter Command Line'

Boot failed! Press any key to enter command line."

It shows my two booting options as Windows Vista and Windows NT/2000/XP.  I have tried installing Ubuntu 3 times off a working CD, the installation finished fine and it gets to the point where it needs to restart to finalize the installation, then when it restarts I get this error.  Any help on this problem is appreciated, thanks.

---

### Post by AduNeButt on 2008-11-27
Any ideas?

---

### Post by TeXtonyx on 2008-11-27
I think those Vista boot options are coming from the MBR,
so delete the MBR and try to install Ubuntu again.

Also delete the Windows partitions and leave the space unallocated.
Run the Ubuntu live cd and use install to largest available continuous
free space (guided) if you have any data partitions to preserve.

Otherwise you can choose to install Ubuntu to the entire disk (guided)
or manually set up the partition structure if you feel confident.

---

### Post by thestig_992 on 2008-11-27
I would reccomend the super grub disk to fix your mbr, provided that ur ubuntu install works perfectly, there should be no reason to reinstall

Be careful though, and back up any data first...

---

### Post by caljohnsmith on 2008-11-27
Those errors you are getting look like they are coming from Grub4DOS, which is the boot loader used in a Ubuntu Wubi installation; Wubi installs Ubuntu inside of Windows so you don't need a separate partition for Ubuntu. How about booting your Live CD (the CD you used to install Ubuntu), open a terminal (Applications > Accessories > Terminal), and post the output of:
```
sudo fdisk -lu
```
Also, for whichever partition is NTFS/FAT32 (your Windows partition), do the following:
```
sudo mount /dev/sda1 /mnt
ls -l /mnt
ls -lR /mnt/ubuntu
```
So replace sda1 above if your Windows is on a different partition. Please post the results and we can work from there if you want.

---

