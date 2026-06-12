---
title: "[SOLVED] Installing Ubuntu on a machine already using Win XP (Dual-Boot System)"
date: 2008-11-30
forum: General Help
---

### Post by JohnFDay on 2008-11-30
I would like to install Ubuntu on my wife's machine.  She's already using Win Xp.

I've checked the <F1> Help with Windows and, fairly typical for Microsoft, the "help" leaves more than a little something to be desired.

How do I go about reducing the partition (C:\) which holds Windows XP so that I can load Ubuntu into the free-space?

I can not find anything of use in the help windows.

Any ideas?

---

### Post by oilchangeguy on 2008-11-30
> **JohnFDay said:**
> I would like to install Ubuntu on my wife's machine.  She's already using Win Xp.

I've checked the <F1> Help with Windows and, fairly typical for Microsoft, the "help" leaves more than a little something to be desired.

How do I go about reducing the partition (C:\) which holds Windows XP so that I can load Ubuntu into the free-space?

I can not find anything of use in the help windows.

Any ideas?

google is your friend. i typed dual boot xp and ubuntu, and got this (amoung others)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by TeXtonyx on 2008-11-30
After you create the partition for Ubuntu by resizing XP, leave
that space unallocated. That when you install Ubuntu with the live
cd you can choose, 'largest continuous free space (guided)'.

This will keep XP safe from being overwritten, in case your wife
is not so understanding. Therefore, you should resize the XP
partition before you install Ubuntu. There is no reason to trust
another live cd option of resizing the XP partition on the fly. 
I don't know if you have a resizing tool like Acronis, but Gparted
will do it, and if you resize before, you will have more control
over the changes made. What you reduce XP by, will become Ubuntu
installed into the unallocated space equal to the XP size reduction.
Don't format that new space, wait till later in the live cd install. 

Now the default live cd install will put grub in the MBR. That 
means one will use the grub menu options to boot XP. If it is
decided to uninstall Ubuntu, it can be a bit of a bother because
the grub boot menu departs with Ubuntu and you can't immediately
boot into XP, you have to fixmbr and fixboot from the Recovery
Console. Also if something big breaks on Ubuntu, then the support
files aren't available for the grub MBR originated boot to XP.

Grub in the MBR will work just fine as long as there is no problem.
Another way is to boot Ubuntu from XP and its boot.ini. That 
means in Step 7, under Advanced, you choose install grub to the
/boot partition. Ubuntu will not immediately boot after that.
Bootpart is a free tool to create a 512 byte boot segment that
resides in root, C:\. It also automatically writes an entry to
the boot.ini file that places Ubuntu on the XP menu boot list.

[http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm)  bootpa26.zip
Unzip and extract bootpart.exe to C:\ so its at C:\>bootpart.exe

Here is a sample of what the output looks like, after C:\bootpart <enter>

Physical number of disk 0 : 56d9f43b
 0 : C:* type=7  (HPFS/NTFS), size= 64974861 KB, Lba Pos=63
 1 : C:  type=5  (Extended), size= 15028807 KB, Lba Pos=130769100
 2 : C:  type=83   (Linux native), size= 14354046 KB, Lba Pos=130769163
 3 : C:  type=5   (Extended), size= 674730 KB, Lba Pos=159477255
 4 : C:  type=82    (Linux swap), size= 674698 KB, Lba Pos=159477318

So your Ubuntu will be on a type=83 Linux Native partition (2).

Thus C:\>bootpart 2 ubuntu.bin Ubuntu 
completes making Ubuntu bootable from XP. There is handy tool
called Super Grub Disk, that enables booting from either OS, too.

This is my boot.ini file with the Ubuntu entry added by Bootpart
automatically along with the ubuntu.bin file created in/at C:\

----------------------------

C:\>type boot.ini

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional"
/NOEXECUTE=OPTIN /FASTDETECT

c:\ubuntu.bin="Ubuntu" 

--------------------------------

You must be careful when you resize a partition. This says Vista but 
will work with XP, it is the proper resizing that counts, not the OS. 

[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

Has pictures which are worth thousands of words, :-)

---

### Post by JohnFDay on 2008-12-17
Thanks for your input.  Very sorry it took so long, but I got involved in several other projects.

Finally got the "dual-boot" system up and running.  Your response was a big help.

Again, thanks!!!

John Day

---

### Post by JohnFDay on 2008-12-17
Thanks for your input.  Very sorry it took so long, but I got involved in several other projects.

Finally got the "dual-boot" system up and running.  Your response was a big help.

Again, thanks!!!

John Day

---

### Post by JohnFDay on 2008-12-17
Thanks.  Took awhile, but I finally got the "dual-boot" system up.

Your info was a big help!

John Day

---

