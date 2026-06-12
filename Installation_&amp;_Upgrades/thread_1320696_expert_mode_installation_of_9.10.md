---
title: "expert mode installation of 9.10"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by weissnich on 2009-11-09
Hi,

is there a way to activate the expert installation mode with the normal 9.10 ubuntu?

The reason is, that I want to install Grub in the root partition and not in the MBR.

---

### Post by realzippy on 2009-11-09
When it comes to partitioning,choose "manual".

---

### Post by weissnich on 2009-11-09
> **realzippy said:**
> When it comes to partitioning,choose "manual".

But this lets you only choose the partitioning and not the location where you want to install Grub, this can not be chosen in the normal installation mode as far as I know.

---

### Post by dhavalbbhatt on 2009-11-09
> **weissnich said:**
> But this lets you only choose the partitioning and not the location where you want to install Grub, this can not be chosen in the normal installation mode as far as I know.

You can create a "grub" partition (essentially /boot) to just install grub and/or kernal images.

---

### Post by grant937 on 2009-11-09
I think during a normal installation of 9.10 there is a selection after you partition in the bottom right hand corner called advanced where you can chose where to install grub.  I can't check right now but maybe someone else can comment.

---

### Post by weissnich on 2009-11-09
> **dhavalbbhatt said:**
> You can create a "grub" partition (essentially /boot) to just install grub and/or kernal images.

I have to install Grub in the root partition because I use the boot-us boot manager.

---

### Post by grant937 on 2009-11-09
I do not know anything about the boot loader you are talking about, but maybe this web page can help. Even though it's title is recover grub there is a section on how to install grub to a partition.  Did you already install 9.10 ?

[http://linuxers.org/howto/how-recover-grub2-ubuntu-910-karmic-koala](http://linuxers.org/howto/how-recover-grub2-ubuntu-910-karmic-koala)

---

### Post by realzippy on 2009-11-09
> **grant937 said:**
> I think during a normal installation of 9.10 there is a selection after you partition in the bottom right hand corner called advanced where you can chose where to install grub.  I can't check right now but maybe someone else can comment.

Yes,such option exists.maybe it is in the end of installation.Forgot.

---

### Post by Ginsu543 on 2009-11-10
You can assign where to install the bootloader at the "Ready to install" window during the installation process. It is the window that lists all the information about the primary user as well as which partitions will be formatted and how. If you look above the "Install" button on the lower right of this screen, you will see a button called "Advanced..." If you click on that, you should get a dialog box that allows you to assign where to install the bootloader.

---

