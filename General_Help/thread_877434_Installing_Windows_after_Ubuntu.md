---
title: "Installing Windows after Ubuntu"
date: 2008-08-01
forum: General Help
---

### Post by solwic on 2008-08-01
Here's my setup:  I've got two hard drives.

500GB SATA (sda) running Ubuntu HH
80GB IDE (sdb) as backup

BIOS is set to boot the SATA drive first.  

I want to install Windows XP to the 80GB drive, then configure GRUB to recognize it and give me the option to boot into it.  I don't want to lose my Ubuntu installation in the process.

Is this possible?  If so, how?

Thanks!

---

### Post by phidia on 2008-08-01
You can just install XP to the 80GB drive-windows will overwrite your MBR. I don't know any way to avoid that-well you could unplug the sata drive but then windows will list the ata drive as the 1st drive and some tweaking may be required.
Either way couuld work but just installing with both drives plugged in will work. After the install completes you will need to boot from the ubuntu install cd and re-install grub. I think re-install grub is a menu option.
If that's a pain get the [super grub disk]("http://www.supergrubdisk.org/") and use that.

---

### Post by solwic on 2008-08-01
> **phidia said:**
> You can just install XP to the 80GB drive-windows will overwrite your MBR. I don't know any way to avoid that-well you could unplug the sata drive but then windows will list the ata drive as the 1st drive and some tweaking may be required.
Either way couuld work but just installing with both drives plugged in will work. After the install completes you will need to boot from the ubuntu install cd and re-install grub. I think re-install grub is a menu option.
If that's a pain get the [super grub disk]("http://www.supergrubdisk.org/") and use that.

Trying that now...will let ya know how it goes.  :D

Thanks!  

:cool:

---

### Post by solwic on 2008-08-01
Nah, didn't work.  Windows setup said it needed to write some files to the SATA drive, but couldn't because it didn't recognize the file system (the whole drive is ext3 with a swap partition).  It wanted me to either use free space on the drive to create an NTFS partition (there is no free space) or delete a partition and create a new NTFS partition.  

Once I got done laughing I rebooted into Ubuntu.  Any ideas?  I'm wondering if it'd be easier to just wipe the 500Gb drive, install Windows, then resize and install Ubuntu.  Take longer, but probably easier in the long run.  :(

Any ideas?  Thanks!

---

### Post by zvacet on 2008-08-01
I know it is trivial question,but did you in bios select to boot IDE drive?If you did it like that I don´t see any reason why Windows wouldn´t install.:)

---

### Post by solwic on 2008-08-01
> **zvacet said:**
> I know it is trivial question,but did you in bios select to boot IDE drive?If you did it like that I don´t see any reason why Windows wouldn´t install.:)

Actually it's a very good question because I did not.  I didn't think it would make a difference, but I can certainly give it a shot.  To be honest, I couldn't figure out why Windows wanted to write files to the Ubuntu drive anyway.  

I'll give it a shot and see how it goes.  Thanks for pointing that out...can't believe I didn't think to try it!

:cool:

---

### Post by solwic on 2008-08-01
> **zvacet said:**
> I know it is trivial question,but did you in bios select to boot IDE drive?If you did it like that I don´t see any reason why Windows wouldn´t install.:)

Same message, telling me to make room on the SATA drive.  I changed the boot order, making the ATA 80GB the first disk in the list.

Guess I'm wiping the drive, installing Windows, then resizing the partition and installing Ubuntu again.  

Yet another reason to hate Windows.  ](*,)

---

