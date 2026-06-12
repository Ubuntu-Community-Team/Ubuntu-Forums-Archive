---
title: "Dual booting w/ GAG"
date: 2006-01-07
forum: Installation &amp; Upgrades
---

### Post by dbpigeon on 2006-01-07
I'm getting a new computer with windows media center 2005 preinstalled, and I wanted to dual boot with GAG, because from what I understand, you can set it to load a certain operating system after a certain time. How can I do this? Should i install GAG, partion the harddrive, and then install ubuntu on the empty partion? and can I partion using GParted from the LiveCD? (i have livecd and install versions of 5.10)

---

### Post by dbpigeon on 2006-01-07
What features are in grub anway? Does it have a way that it can boot a certain OS after waiting for a bit?

---

### Post by Herman on 2006-01-07
dbpigeon, hello, you aksed:
> I'm getting a new computer with windows media center 2005 preinstalled, and I wanted to dual boot with GAG, because from what I understand, you can set it to load a certain operating system after a certain time. How can I do this? Should i install GAG, partion the harddrive, and then install ubuntu on the empty partion? and can I partion using GParted from the LiveCD? (i have livecd and install versions of 5.10) It would be simpler for you to just use GRUB as your bootloader, you can configure GRUB to load whichever operating system you like and also change the timer setting and do quite a few other tricks with GRUB as well. This is all done by editing GRUB's menu.lst file, after Ubuntu is installed.

GAG is also a good bootloader if you don't want to use GRUB for some reason. 
If you want to use GAG, you should make a GAG CD or floppy disk beforehand, so it will be ready to re-boot with in the middlle of your Ubuntu install.
Choose 'Go Back', at the point when the installer asks you for permission to install GRUB to the Master Boot Record, and scroll down one line in the Ubuntu Installer Main Menu, and choose to install Lilo boot loader instead. Then, in the Install Lilo window, choose to install Lilo to your new Ubuntu partition.
Don't forget, of course, you will need to have allowed booting from your floppy drive in BIOS beforehand hand as well, if it is a GAG boot floppy that you plan to use. Another thing you can do is use GAG on 'System Rescue CD' to reboot with if you forgot to change your BIOS settngs and you are stuck. If you already know how to configure GAG at this point, it will be easier for you, but it does include good instructions you can read as well, so it should be easy enough regardless.
GAG does have a few advantages, even if you install GAG to MBR, it will install its 'stage1' to MBR, and the rest of it installs in your first track of your hard disk, not to your Ubuntu partition. That means if you like to re-arrange your partitions a lot and are always installing and uninstalling different operating systems, you will always have your boot loader functioning and able to be re-configured to suit any new situation you may create for yourself. If you had installed GRUB, by comparison, and you uninstall or move Ubuntu, you might temporarily loose GRUB, until you have time to re-install GRUB, which is just a little more work than re-configuring GAG, which is very easy.
For me, it makes more sense to use GAG from floppy disks though.
You can use GParted from the Live CD if you like, or you can use the install CD to do the partitioning for you, whichever you prefer.
If you click on my signature link, you will find quite a lot of unofficial information about the subjects you are asking about, except for GParted. I like GParted, but it is so nice and simple to use, it probably doesn't need any extra explanation.:D (Herman).

---

### Post by dbpigeon on 2006-01-07
[QUOTE=Herman]dbpigeon, hello, you aksed:
 It would be simpler for you to just use GRUB as your bootloader, you can configure GRUB to load whichever operating system you like and also change the timer setting and do quite a few other tricks with GRUB as well. This is all done by editing GRUB's menu.lst file, after Ubuntu is installed.

GAG is also a good bootloader if you don't want to use GRUB for some reason. 
If you want to use GAG, you should make a GAG CD or floppy disk beforehand, so it will be ready to re-boot with in the middlle of your Ubuntu install.
Choose 'Go Back', at the point when the installer asks you for permission to install GRUB to the Master Boot Record, and scroll down one line in the Ubuntu Installer Main Menu, and choose to install Lilo boot loader instead. Then, in the Install Lilo window, choose to install Lilo to your new Ubuntu partition.
Don't forget, of course, you will need to have allowed booting from your floppy drive in BIOS beforehand hand as well, if it is a GAG boot floppy that you plan to use. Another thing you can do is use GAG on 'System Rescue CD' to reboot with if you forgot to change your BIOS settngs and you are stuck. If you already know how to configure GAG at this point, it will be easier for you, but it does include good instructions you can read as well, so it should be easy enough regardless.
GAG does have a few advantages, even if you install GAG to MBR, it will install its 'stage1' to MBR, and the rest of it installs in your first track of your hard disk, not to your Ubuntu partition. That means if you like to re-arrange your partitions a lot and are always installing and uninstalling different operating systems, you will always have your boot loader functioning and able to be re-configured to suit any new situation you may create for yourself. If you had installed GRUB, by comparison, and you uninstall or move Ubuntu, you might temporarily loose GRUB, until you have time to re-install GRUB, which is just a little more work than re-configuring GAG, which is very easy.
For me, it makes more sense to use GAG from floppy disks though.
You can use GParted from the Live CD if you like, or you can use the install CD to do the partitioning for you, whichever you prefer.
If you click on my signature link, you will find quite a lot of unofficial information about the subjects you are asking about, except for GParted. I like GParted, but it is so nice and simple to use, it probably doesn't need any extra explanation.:D (Herman).[/QUOTE]

Ok, thanks a lot. That was all I needed.

---

