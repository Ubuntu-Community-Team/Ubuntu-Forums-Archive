---
title: "Big Problem! Need help plz!"
date: 2008-08-08
forum: General Help
---

### Post by Holderlin on 2008-08-08
Hello everyone! Im losing my sanity here trying to fix this. The problems is like this: I`d installed in mi HD Ubuntu 7.04, which take up around 140GB, and Windows XP, which take up around 100GB. In the last few days i needed that ubuntu space in that specific HD so i got the great idea of deleting the partitions from the Disk administrator of Windows and formatting from there in NTFS. THE BIG PROBLEM came the following morning when i wake up and try to acces Windows, the PC boot but when it was time for the bios to give the OS the control a black screen told me the Grub was missing! Do i have to install the windows booter in the MBR IM SO LOST

I have no idea how to fix this and im losing my mind. Please, please, please help me. Thank you in advanced!

---

### Post by Holderlin on 2008-08-08
How quickly you go down here! An up for myself! 

Please help!

---

### Post by tuxxy on 2008-08-08
Install GRUB

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Elfy on 2008-08-08
No - use the win disc to boot it's recovery and fixmbr. IF that doesn't help becuase you don't have the disc you can download and burn supergrub and it has an option to fix windows mbr.

If though you intend to reinstall ubuntu it will reinstall grub.

---

### Post by Sycron on 2008-08-08
I tried with supergrub an it fixed my problem instantly :) .

---

### Post by Holderlin on 2008-08-08
I dont have a LiveCD and  what i want to leave clear: in that PC i dont want linux anymore.I got a new pc so i will run linux there, but in this pc im talking about i only want to have Windows.

Is there a way to replace the damage grub for whatever botmanager windows has???? I have a lot of very important things for me there.

Help!

---

### Post by Sycron on 2008-08-08
Try with *supergrub* or* windows xp instalation cd with recovery console*...

---

### Post by Elfy on 2008-08-08
> **Sycron said:**
> Try with *supergrub* or* windows xp instalation cd with recovery console*...

It's the only way I know of now you've deleted the linux - if you haven't got the win disc get supergrub - you have to burn it as an iso so you can boot with it.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Holderlin on 2008-08-08
How do i acces the recovery console you are talking about. I got the XP installation CD but i just dont know how to acce the recovery console.

---

### Post by Elfy on 2008-08-08
Going from memory as it is a long time ago...

Boot with the windisc - let it go through all the interminable rubbish and I think you should be asked if you want to install or go to recovery console - choose recovery and let it get set up - I think the command you need is fixmbr or it might be fixboot can never remember - help is \help I think.

There is a ms knowledge page I'll go look


Edit - this should help you out [http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058)

Use fixboot it seems

---

