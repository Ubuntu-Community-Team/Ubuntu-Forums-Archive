---
title: "GRUB install to root of Ubuntu"
date: 2009-04-05
forum: Installation &amp; Upgrades
---

### Post by GregB3 on 2009-04-05
I am trying to install GRUB to the root of Ubuntu during the installation of Ubuntu.  When I get to the step where I press the Advanced button the installer returns a value of (hd0).  My system's disk partition layout is as follows:

sda1  NTFS  Windows XP Pro
sda2  extended
sda5  ext3  /  MEPIS 8 Linux
sda6  Linux-swap
sda7  ext3  / for Ubuntu install
sda8  ext3  /home for Ubuntu install
sda9  ext3  /home for MEPIS 8 Linux

If I want to install GRUB to the / of Ubuntu would I enter /dev/sda7 in the GRUB install response box?  Will all versions of the Ubuntu installer accept and carry out user input into this response box? I've read about there being an alternative CD.  Would I need to have the alternative CD to install GRUB to the root partition?

I want to use NTLDR as my primary bootloader.  There is a freeware utility called BootPart that can configure BOOT.INI to load Linux using the NTLDR.  It handles everything that needs to be done to configure NTLDR to chainload the root installed GRUB of the Linux OS.  This way if it becomes necessary to reinstall Windows XP Pro, access to the Linux installs can be restored quickly by running BootPart.  It was used to add Linux to a quad boot 32-bit PC running Windows 98SE, Windows XP Pro, MEPIS 8, and PCLinuxOS2009.  It was also used to add MEPIS 8 to the above mentioned PC, which is an AMD64 PC.

I am also wondering what the scope of action of the partitioning section of the installer is. If manual is selected will the Ubuntu installer only modify the selected partitions?  I don't want to loose my Windows and MEPIS installs.

---

### Post by logos34 on 2009-04-05
> **GregB3 said:**
> 
If I want to install GRUB to the / of Ubuntu would I enter /dev/sda7 in the GRUB install response box?  Will all versions of the Ubuntu installer accept and carry out user input into this response box? I've read about there being an alternative CD.  Would I need to have the alternative CD to install GRUB to the root partition?

yes, '/dev/sda7'. Yes.  You can use the live cd or alt cd to install grub wherever

> 
I am also wondering what the scope of action of the partitioning section of the installer is. If manual is selected will the Ubuntu installer only modify the selected partitions?  I don't want to loose my Windows and MEPIS installs.

As long as you indicate / and /swap, and do NOT check 'format' box for windows partitions, the latter shouldbe fine.

---

### Post by ronparent on 2009-04-05
I just would advise caution in placing grub on sda7. Depending on your bios, there is a 134 Gb limit on some older computers. If that should be the case you can install grub in another partition closer to the beggining of the disk, or, alternatively create a small partion for grub by shrinking a partition.

---

### Post by GregB3 on 2009-04-05
Thanks for the replies.  The partition sizes in Gparted are:

sda1 NTFS Windows XP Pro             97.65GiB
sda2 extended                       200.43GiB
sda5 ext3 / MEPIS 8 Linux            10GiB
sda6 Linux-swap                       1GiB
sda7 ext3 / for Ubuntu install       10GiB
sda8 ext3 /home for Ubuntu install   20GiB  
sda9 ext3 /home for MEPIS 8 Linux   159.42GiB

If the Linux partitions can be added directly to the Windows partition the / Ubuntu install should be entirely below the 134GB limit mentioned.  The AMD64 PC is about a year and a half old and has an AM2 CPU socket.  I plan on doing a whole disk image backup before doing the Ubuntu installation.  

Thanks again for the information.

---

### Post by logos34 on 2009-04-05
the bios limit isn't an issue on newer boards, so you'll be fine.

The only thing I would add is you might install fs-driver so you can access your linux partitions from windows (or maybe you already have it, dunno).

good luck

---

