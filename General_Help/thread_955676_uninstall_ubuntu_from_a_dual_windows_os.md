---
title: "uninstall ubuntu from a dual windows os"
date: 2008-10-22
forum: General Help
---

### Post by Chamalo on 2008-10-22
Hi,

I got Ubuntu and Vista on my comp as a dual boot. I went in Vista and delete the two partitions allocated to ubuntu and I can't switch on anymore. I got the message:

Grub loading...

Grub loading...
Error 17

That's it! and no key responds, either the e or the c...

What could i do???

Cheers! 
The Cham:)

---

### Post by No-Neck on 2008-10-22
This has happened because your Master Boot Record (MBR) is pointing to GRUB, which was pointing to both Windows and Ubuntu. You have just wiped out the parition that countained GRUB.

You will need to boot up your Windows CD and do a repair, or something similar, search google for 'repair mbr vista' or 'repair ntldr' or 'reinstall mbr', etc, etc. It shouldn't be too difficult.

---

### Post by C.S.Cameron on 2008-10-22
If you have your windows install disk you can go to emergency repair console and type 'fixmbr'.

---

### Post by caljohnsmith on 2008-10-22
If you have your Vista Install CD, just go to the command line and run:
```
bootrec /fixmbr
```
Or if you don't have that, you can download the [Super Grub Disk]("http://www.supergrubdisk.org/"), and it has an option to install a Windows MBR. Let us know how it goes. :)

---

### Post by SSDF on 2008-10-23
I actually Have this problem as well,
I installed ubuntu after partitioning the vista section and it installed fine however I couldn't get it connected to the internet amoung other things, and I wasn't sure how to uninstall it.
Thus I checked here, so if I havn't deleted the partitions what should I do ?

note: I don't have the vista disk

---

