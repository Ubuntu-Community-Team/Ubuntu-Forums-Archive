---
title: "grub help"
date: 2008-11-16
forum: General Help
---

### Post by orlyr21 on 2008-11-16
Im trying to triple boot windows vista, ubuntu 8.10, and fedora 9.

the problem is, i installed fedora 9 last and when i try to boot up my computer the fedora boot loader automatically comes up and only recognises fedora, and windows.
i fixed this by reinstalling grub loader from my ubuntu live cd, and now grub loader only recognizes ubuntu and windows.

does anyone know how to force grub loader into recognising fedora 9 as well as ubuntu, and windows?

oh and yes, i installed all 3 OS's correctly in 3 different partitions on my hard drive.

---

### Post by Marcus Derekus on 2008-11-16
Sorry for adding this post but i thought i had the answer but i dont

---

### Post by Marius Derekus on 2008-11-16
Same here (were bro's, we think the same) Sorry.

---

### Post by boof1988 on 2008-11-16
> **orlyr21 said:**
> Im trying to triple boot windows vista, ubuntu 8.10, and fedora 9.

the problem is, i installed fedora 9 last and when i try to boot up my computer the fedora boot loader automatically comes up and only recognises fedora, and windows.
i fixed this by reinstalling grub loader from my ubuntu live cd, and now grub loader only recognizes ubuntu and windows.

does anyone know how to force grub loader into recognising fedora 9 as well as ubuntu, and windows?

oh and yes, i installed all 3 OS's correctly in 3 different partitions on my hard drive.

Use this (in the Terminal in Ubuntu) to get the available drives/partitions:

```
sudo fdisk -l
```

Make sure you know your root and boot partitions for Fedora.

Use this (in Terminal in Ubuntu) [or some other way] to edit GRUB's menu.lst and add neccessary lines to boot Fedora:

```
sudo nano -B /boot/grub/menu.lst
```

[Note: The -B in this command makes a backup of menu.lst and labels it menu.lst~]

Hope this helps some... I had a hard time understanding all the boot stuff.  And I'm still mostly clueless but I'm learning.

References:
[hermanzone's GRUB page](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by TeXtonyx on 2008-11-16
Hi,

I think a quick fix is to download Easybcd and add both Fedoara
and Ubuntu under the Linux section of its add OS.

I exchanged a hard drive which had OpenSuse on it for my second 
drive. Then I installed Ubuntu on my first drive and I'll show
you my /etc/grub/menu.lst relevant parts

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=79c7fc43-8f76-49e6-8214-67cc4c71e5b1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

-----------------

# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1

-----------------------------

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		openSUSE 11.0 (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.25.5-1.1-default root=/dev/disk/by-id/scsi-SATA_Maxtor_6E020L0_E13LK8CE-part1 resume=/dev/sda7 splash=silent showopts vga=0x317 
initrd		/boot/initrd-2.6.25.5-1.1-default
savedefault
boot

---------------------------

TeX: Under the Windows section I don't think it matters what the
title is, it could be Vista, what matters is the root information.

As you know both the Ubuntu and Fedora grubs cannot inhabit the
MBR at the same time. So I get around this by installing grub
to the /boot partition. I used to dual boot Redhat6 and this is
the method I used. Briefly, about a year ago I used Fedora 9 
but I don't remember if I used this method. Sometimes installing
to the /boot partition is obscured during the install menus. 

See where it says, root (hd1,0), that means I have grub in the
/boot partition rather than the MBR of the second drive = (hd1)

In your case with all the OS on one drive and without the output
of , sudo fdisk -l , your third OS and second Linux OS, might be
on (hd0,6) which is sda7, the partition numbers are one lower.

So my solution is to reinstall grub to either the /boot partition
of Fedora or Ubuntu and put grub in the MBR for the other OS.
I'm more sure this will work with Ubuntu grub in /boot partition
and Fedora grub reinstalled to the MBR.

Since I have a strong background in Windows and dual booting, I
install grub to all Linux /boot partitions and use the Windows boot- 
loader with Easybcd or with XP, Bootpart. This is very reliable on 
one drive as in your situation. So, I'm just adequate when it comes 
to using grub. I think my advice will work but the grub experts
may improve the advice. My proof of concept = my menu.lst print.
I've seen nice solutions which use a dedicated /grub partition.

---

### Post by Marcus Derekus on 2008-11-17
Did you install Grub with Fedora so that Fedora has its own menu.lst? If Fedora has a menu.lst, you can boot Fedora from Ubuntu by adding the following to Ubuntu's menu.lst:
Code:

```
title Fedora Grub Menu
configfile (hdX,Y)/PATH/TO/FEDORA'S/menu.lst
```

And change (hdX,Y) to the Fedora drive/partition. If you want help, how about posting:
Code:

```
sudo fdisk -l
```

And identify your partitions.

---

