---
title: "Did rebuild and want to run Ubuntu again but have Acronis TI"
date: 2008-08-26
forum: General Help
---

### Post by Universal344 on 2008-08-26
I recently experienced problems with my copy of Windows Vista Ultimate.  I decided to do a complete reformat of my disk and reinstall Vista.  Now I am beginning to think I may want to dual-boot with Ubuntu again.  However, I have Acronis True Image 10 Home installed and Acronis Boot Recovery Manager turned on (I think thats the name but in case I'm wrong its the feature that enables me to load my image before windows boots).  From what I've read it seems that if I install Ubuntu after I have Windows and Acronis installed GRUB will wipe Boot Recovery Manager off the Master Boot record.  Is there a way to keep boot recovery manager and still install GRUB?

I don't know much about the MBR or how things like GRUB or Acronis Boot Recovery Manager work.

Thanks for your help!

---

### Post by jerome1232 on 2008-08-26
You can create a small partition ~1GB and mount it as /boot(that's generous) and right before you give the okay to install Ubuntu there's an advanced options button, click that and tell it to install grub to the /boot partition.

Somehow you will have to tell acronis to have an option to boot the partition /boot is on.

I haven't tried this and don't have access to a VM at the moment to confirm/deny that this will work so use at your own risk

---

### Post by Universal344 on 2008-08-26
Thanks but I think I need Acronis Disk Director to boot the /boot partition and I use True Image.  Does anyone know if this is true?

---

### Post by jerome1232 on 2008-08-26
Yeah your current setup is Arconis Disk Director is the boot loader and it boots the Acronis True Image which is just a disk image correct?

So I think you would configure Acronis Disk Director to have an option to boot your True Image, and another option to boot /boot, When it boot's /boot, grub will start up and automatically boot Ubuntu.

Unless your wanting Ubuntu to be another image, in which case I have no idea. That's more dependent on this Acronis software.

---

### Post by Universal344 on 2008-09-06
I have Acronis True Image not Disk Director on my machine (although I think I may have a copy of Disk Director somewhere).  But, if possible, a simpler solution would be appreciated.

---

### Post by Universal344 on 2008-09-06
Anyone?

---

### Post by Universal344 on 2008-09-07
Last Bump (sigh)

---

### Post by gdboytyler on 2008-09-07
What you should do is re-install Windows the way you normally would with Acronis.

Then install Ubuntu without changing the MBR:
[http://ubuntuforums.org/showthread.php?t=56723]("http://ubuntuforums.org/showthread.php?t=56723")

This way, you can continue to use your Boot Recovery Manager.

---

### Post by Universal344 on 2008-09-08
I successfully disabled startup recovery manager by fixing my MBR through Windows RE.  I found instructions on Acronis's website about making GRUB and startup recovery manager coexist, but the instructions are very confusing to me.  They tell me to install GRUB into a folder after installing Ubuntu (I think).  Any clarification is very much appreciated.  Thanks!

[http://www.acronis.de/enterprise/support/kb/articles/102/](http://www.acronis.de/enterprise/support/kb/articles/102/)

---

### Post by diver858 on 2008-09-15
> **Universal344 said:**
> I successfully disabled startup recovery manager by fixing my MBR through Windows RE.  I found instructions on Acronis's website about making GRUB and startup recovery manager coexist, but the instructions are very confusing to me.  They tell me to install GRUB into a folder after installing Ubuntu (I think).  Any clarification is very much appreciated.  Thanks!

[http://www.acronis.de/enterprise/support/kb/articles/102/](http://www.acronis.de/enterprise/support/kb/articles/102/)


Dosen't work for me either - WinXP, Ubuntu 8.0.4; for now, I gave up: wiped out Recovery Manager and added TI v11 to Grub: [http://ubuntuforums.org/showthread.php?t=449167&highlight=Adding+Acronis+Grub+list](http://ubuntuforums.org/showthread.php?t=449167&highlight=Adding+Acronis+Grub+list)

Would also appreciate some help

---

