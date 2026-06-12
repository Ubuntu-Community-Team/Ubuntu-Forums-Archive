---
title: "grub 17 error, HELP!"
date: 2008-08-22
forum: General Help
---

### Post by nkobel003 on 2008-08-22
I deleted the partition with ubuntu through windows, and now when I start windows, I get "error 17" in grub. I know why, but is there a way to just boot directly to the windows partition instead of using grub?

---

### Post by Elfy on 2008-08-22
You need to fix the windows boot - use your win disc to do so - recovery mode in win2k and xp - fixmbr

Not sure about vista though..

If you haven't got the disc you can use [supergrub]("http://www.supergrubdisk.org/")

---

### Post by caljohnsmith on 2008-08-22
> **forestpixie said:**
> You need to fix the windows boot - use your win disc to do so - recovery mode in win2k and xp - fixboot

Not sure about vista though..

If you haven't got the disc you can use [supergrub]("http://www.supergrubdisk.org/")
Actually, I think you mean "fixmbr" instead of "fixboot"; fixmbr will reinstall the Windows boot loader to the master boot sector (MBR), while fixboot fixes just the boot sector of the Windows partition. So if you want to get rid of Grub and have only Windows, I believe you want to run fixmbr so you can overwrite Grub. 

Or of course you can just use the Super Grub Disk, like you suggest forestpixie, to reinstall the Windows MBR and not worry about what the command is called. :)

---

### Post by Elfy on 2008-08-22
whoops sorry - long time ago - I'll change it :oops:

But yes supergrub is good to have even for those windows moments :)

---

