---
title: "Windows 7 booting automatically"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by g2no11ah2 on 2009-11-02
Hi, I recently upgraded to Windows 7 on my other partition and now I don't have an option to boot to my Ubuntu OS.  Is there a way to get that option back?

---

### Post by James2k on 2009-11-02
Sounds like you've lost your GRUB loader. You will need to boot from a Ubuntu Live CD and restore the grub.

This should help:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by ram130 on 2009-11-02
> **James2k said:**
> Sounds like you've lost your GRUB loader. You will need to boot from a Ubuntu Live CD and restore the grub.

This should help:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

what about grub2 restore? don't forget the new ubuntu uses it. Also james2k are you using Ubuntu 9.10?

---

### Post by James2k on 2009-11-02
Yes sorry there is that option to, and yes I am.

---

### Post by g2no11ah2 on 2009-11-24
What is the method for grub2 restore?

---

### Post by ram130 on 2009-11-25
I recently had to restore it myself two days ago after a reinstall of windows, here is **how to restore grub2:**

> You will need a LIVE cd if you are going to recover an Ubuntu Box.Download Ubuntu Jaunty, Karmic whatever you want.Open the system with Live CD (I assume you are using Ubuntu Live CD).Press Alt+F2 and enter gnome-terminal command.And continue by entering :

$sudo fdisk -l

This will show your partition table.Here is my table to understand it better :

/dev/sda1 29 8369 66999082+ 83 Linux
/dev/sda2 * 8370 13995 45190845 7 HPFS/NTFS
/dev/sda3 13996 14593 4803435 5 Extended
/dev/sda5 13996 14593 4803403+ 82 Linux swap / Solaris

Now i will mount Linux (sda1 here), i have no external boot partition as you can see.(IF YOU HAVE external one, do not forget to mount it! )

$sudo mount /dev/sda1 /mnt
$sudo mount --bind /dev /mnt/dev
$sudo mount --bind /proc /mnt/proc

The following command is optional (it copies resolv.conf)

$sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

Now chroot into the enviroment we made :

sudo chroot /mnt

After chrooting, you do not need to add sudo before your commands because from now, you will run commands as root.

You may want to edit /etc/default/grub file to fit your system (timeout options etc)

#nano -w /etc/default/grub

Play with the options if you want.(But do not forget to give grub-update command if you saved it ;) )

Now install/recover Grub2 via :

#grub-install /dev/sda

command.However you may get errors with that code like me.If so please use this command :

#grub-install --recheck /dev/sda

Now you can exit the chroot, umount the system and reboot your box :

#exit
$sudo umount /mnt/dev
$sudo umount /mnt/proc
$sudo umount /mnt
$sudo reboot

[site]("http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html")

---

