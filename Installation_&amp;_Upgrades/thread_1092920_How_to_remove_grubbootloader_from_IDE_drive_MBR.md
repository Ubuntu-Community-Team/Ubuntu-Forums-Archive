---
title: "How to remove grub/bootloader from IDE drive MBR?"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by Nixie Pixel on 2009-03-10
Hi, I am using an old IDE drive in a newly built system, and I have some problems.  I'm trying to get my primary SATA drive to boot, but BIOS won't let me choose it as my boot HDD because I have an IDE drive with an MBR on it.  That MBR apparently contains GRUB (which fails when it is run), but I don't know why - it was never used as a boot drive.  I did format a portion of it with NTFS and another portion with ext3, but I never booted to it, never thought I put GRUB on it, and never thought its boot sector would be altered.

Anyway, it does have a bunch of data that I want to keep, so I don't want to mess up my partition table.  I can't very well hot swap it in, so I'm sort of stuck, as I'm really unfamiliar with boot sectors and how to manipulate them.

Is there a way I can use an Ubuntu Live CD to remove GRUB or to otherwise make it so I can boot to my SATA drive while my IDE drive is plugged in?  The SATA drive currently has Vista Ultimate 64 on it.

Thanks!

---

### Post by Neo_The_User on 2009-03-10
You want to completely remove grub and have no boot loader???

---

### Post by meierfra. on 2009-03-10
> Is there a way I can use an Ubuntu Live CD to remove GRUB 

Yes. Boot from the LiveCD, open a terminal (Applications->Accessories->Terminal) and post the  output of

```
sudo fdisk -lu
```

and I can tell you the exact command to erase Grub.

---

### Post by Neo_The_User on 2009-03-10
Message blanked by Neo_The_User due to wrong bad command

---

### Post by orethrius on 2009-03-10
Oh, I hope there's another bootloader to take over... ;)

---

### Post by Neo_The_User on 2009-03-10
> **orethrius said:**
> Oh, I hope there's another bootloader to take over... ;)

I know right?

---

### Post by meierfra. on 2009-03-10
> I hope there's another bootloader to take over..
Yes, there is: On the Sata drive. Most bios, if they don't find a boot loader on the first hard drive, will try to boot the second hard drive.

---

### Post by Neo_The_User on 2009-03-10
Message edited.

---

### Post by ridetheteapot on 2009-03-10
meierfra. is smart.

meanwhile you definatly do not want to wipe the whole mbr 512bytes; with this stuff it pays to be cautious. there is a smaller section of the mbr for code, thats what you are aiming for. the whole mbr 512b aka partition sector also includes the partition table :) now wiping that would hurt

---

