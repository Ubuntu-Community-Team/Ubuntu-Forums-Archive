---
title: "when and how to assign grub location at setup?"
date: 2005-12-22
forum: Installation &amp; Upgrades
---

### Post by someuser77 on 2005-12-22
I am about to install Ubuntu on a computer that already has Windows 2000 on it.
I would like to install Ubuntu on a secondary HD and put Grub on the first partition there, so the Master Boot Record will remain MS`s, and i will add an entry to boot.ini.
My question is what must i do to change the default location for grub?

---

### Post by Sutekh on 2005-12-22
At some point (late) in the install, you will told that the installer has detected other OSs, and will ask you if you want to install GRUB on the MBR.  You should say no, then you can choose where you'd like it installed.  

It should go on the / partition of your new Ubuntu installation (or /boot if you created that partition).  So when you are doing the partitioning earlier in the installation, make note of the hard drive and partition that Ubuntu is installed on.

For me, I had two hard drives, one IDE drive (with WinXP), which was designated by the installer as hda, and one SATA drive (for Ubuntu) designated sda.  Ubuntu (and the / partition) was installed on the first partition of the SATA disc.  So I told the installer to put GRUB on 
```
/dev/sda1
```

What hard drives are you using for the installation?

---

### Post by someuser77 on 2005-12-22
Well, I have a 20GB Seagate ([ST320414A](http://www.seagate.com/support/disc/ata/st320414a.html)) and a 120GB Maxtor ([6Y120P0](http://www.maxtor.com/portal/site/Maxtor/menuitem.5d2b41d3cef51dfe29dd10a191346068/?channelpath=/en_us/Support/Product%20Support/Desktop%20Storage/DiamondMax%20Family/DiamondMax%20Plus%209)).
The Seagate is the master from where Windows boots, and i was planing to install Ubuntu on the first 60GB of the Maxtor HD, the rest will be a FAT32/NTFS share.

---

### Post by Sutekh on 2005-12-22
Okay, so the installer will probably see your discs as;

Seagate - hda (hd1)
Maxtor - sda (sd1)

If you put GRUB on the Maxtor (sda), then to use the GRUB bootloader (and choose between Ubuntu and Windows), the Maxtor drive *must* be the priority (1st) boot device in your BIOS.  Otherwise when your PC boots, it will look at the Seagate (hda) first and it will use the Windows bootloader missing GRUB completely. :mad: 

Having a share partition would be a good idea too.  Have you worked out how you want to divide the space for Ubuntu?

---

### Post by someuser77 on 2005-12-22
[quote="Sutekh"]when your PC boots, it will look at the Seagate (hda) first and it will use the Windows boot loader missing GRUB completely.[/quote]
I was planing to use "dd":
```
dd if=/dev/hda7 of=linux.lod bs=512 count=1
```
(where /dev/hda7 is the boot partition) to save and copy linux.lod to the windows partition and add it to boot.ini so i will be able to load Linux from the windows boot manager.

[quote="Sutekh"]Have you worked out how you want to divide the space for Ubuntu?[/quote]
/boot - 100MB
/(root) - 20GB
/home - 20GB
/var - 20GB
swap - 1GB

I'm open for suggestions.
btw, thanks for the help. :)

---

### Post by Sutekh on 2005-12-22
[QUOTE=someuser77]I was planing to use "dd":
```
dd if=/dev/hda7 of=linux.lod bs=512 count=1
```
(where /dev/hda7 is the boot partition) to save and copy linux.lod to the windows partition and add it to boot.ini so i will be able to load Linux from the windows boot manager.
[/QUOTE]
Well I don't know anything about that, but it looks like you do!

[QUOTE=someuser77]
/boot - 100MB
/(root) - 20GB
/home - 20GB
/var - 20GB
swap - 1GB

I'm open for suggestions.
btw, thanks for the help. :)[/QUOTE]
I like.  What do you use /var for?

---

### Post by someuser77 on 2005-12-22
[quote="Sutekh"]What do you use /var for?[/quote]
My bad. :( 
Its not /var, its /usr. And afaik all the user data goes there, like apps and so. correct me if i'm wrong.

---

### Post by Sutekh on 2005-12-22
Yeah /usr has apps and stuff.  Mine is quite big at the moment ~4GB.

/var actually has quite a bit of stuff too.  The main thing for me in /var is the apt-get cache, and packages.

---

### Post by someuser77 on 2005-12-22
So you think i should give each 10GB or so?

---

### Post by Sutekh on 2005-12-22
I think you could give less to /var and more to /usr.  My /var is using just over 1GB, and most of that is apt packages, which I don't really need.

Just to be clear, I didn't set aside separate partitions for /usr or /var or anything.  Just /  /boot  /home  /swap.  So I don't have to worry about /usr filling up.  

There should be some threads around with suggestions on sizes of extra partitions like /usr.

---

