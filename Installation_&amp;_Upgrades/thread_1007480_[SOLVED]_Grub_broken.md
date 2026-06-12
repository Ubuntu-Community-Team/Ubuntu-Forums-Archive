---
title: "[SOLVED] Grub broken"
date: 2008-12-10
forum: Installation &amp; Upgrades
---

### Post by captkirk on 2008-12-10
I upgraded to 8.10 the other day.  My system was not performing very well, so I did a clean install of ubuntu 8.10.  I can no longer boot either ubuntu or Windows XP on my dual boot system. I tried to restore grub using the instructions at [COLOR="Blue"]_[http://ubuntuforums.org/showthread.php?t=965672]("http://ubuntuforums.org/showthread.php?t=965672")_[/COLOR]

I am getting an error when I try step 6.  Here is the output:

```
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.

```

I am willing to follow some directions, but I must not be using the correct search term.  Could someone give me some other places to look?

---

### Post by ajgreeny on 2008-12-10
Run the live cd and show us the output of ```
sudo fdisk -l
``` and then mount your hard disk, and navigating to that, show us just the menu entries at the bottom of the */boot/grub/menu.lst*.  It may give a clue about what is going on here.

---

### Post by captkirk on 2008-12-10
> **ajgreeny said:**
> Run the live cd and show us the output of ```
sudo fdisk -l
``` and then mount your hard disk, and navigating to that, show us just the menu entries at the bottom of the */boot/grub/menu.lst*.  It may give a clue about what is going on here.

sudo fkisk -l gives:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf12ff12f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13374   107426623+   7  HPFS/NTFS
/dev/sda2           13375       13617     1951897+  82  Linux swap / Solaris
/dev/sda3           13618       16049    19535040   83  Linux
/dev/sda4           16050       30401   115282440    b  W95 FAT32

```

Ironically, I don't seem to have a /boot/grub/menu.lst file.  I guess that is part of the problem?  :confused: The only file in that directory is device.map.

Thanks for helping.

---

### Post by Tlingit on 2008-12-10
I guess i am having problems with grub even installing from the Intrepid Ibex distro both x32 and x64.

---

### Post by caljohnsmith on 2008-12-10
Captkirk, when you installed Ubuntu, did you change any of the settings in the "advanced" button near the end of the installation? Because if not, Grub should have been properly installed, and you would have a menu.lst and all of Grub's other boot files. How about reinstalling, but don't change any of the settings under the "advanced" button. Let us know how it goes.

---

### Post by falcon61102 on 2008-12-10
captkirk,

When you installed the second time, do you remember if you checked the box to install the GRUB?  

And could it be that GRUB installed itself onto another partition?

Try running the following and seeing what comes up:
```
sudo grub
find /boot/grub/stage1
```

Also, you may want to look into the Super Grub Disk ( [www.supergrubdisk.org](www.supergrubdisk.org) ) as it can really simplify things in the installation of the GRUB in cases like this.

---

### Post by Tlingit on 2008-12-10
"Im not trying to thread jack" but this IS the place to post"
falcon61102 I tried doing what you have sugested in both x32 and x64.

First grub finds stage1 on (hd1,7) which is very odd?? and that is booting from a live cd. after install i get a system boot failure on both x32 and x64.

Every other distro installs just fine and runs great any ideas??/ thanks

---

### Post by ajgreeny on 2008-12-11
> and then mount your hard disk, and navigating to that, show us just the menu entries at the bottom of the */boot/grub/menu.lst*.  It may give a clue about what is going on here.     Are you sure you did this and that you are not looking at, or rather for, the menu.lst file in your live CD, which I don't think has such a file.  You need to find the file on your hard disk somewhere or other.

---

### Post by captkirk on 2008-12-12
All, thanks for your help.  I want to answer all of the questions.

1) I took the default options for grub.  I am not smart enough to mess around with grub.

2) I don´t think grub installed on another partition.

3) I was not looking at the livecd.  I am pretty sure only because I was really trying to check.

I finally reinstalled and it worked this time.  I had to go back into bios and tell the bios to boot again from the hard drive.  I then had to wait for a prompt (from grub?) to boot from the cd.  Once I was on the cd, I reinstalled with no problems.  

This leads to a new question: did I ever need to switch the bios to cd boot, or should I have left that alone?  I am using an nvidia nforce 2, if the bios makes any difference.  Also, was that prompt from grub?  What if I want to boot something else, how do I make that happen?  Can someone point me to a basic faq or something on grub?  It seems I can only find very high level or detail level of grub and not much in between.


Thanks again for your help! :p

---

### Post by caljohnsmith on 2008-12-12
> **captkirk said:**
> 
This leads to a new question: did I ever need to switch the bios to cd boot, or should I have left that alone?  I am using an nvidia nforce 2, if the bios makes any difference.  Also, was that prompt from grub?  What if I want to boot something else, how do I make that happen?  Can someone point me to a basic faq or something on grub?  It seems I can only find very high level or detail level of grub and not much in between.


Thanks again for your help! :p
Here's some good information on Grub:

[http://www.users.bigpond.net.au/hermanzone/p15.htm](http://www.users.bigpond.net.au/hermanzone/p15.htm)

About changing your BIOS to boot the CD, if your BIOS isn't all ready set to boot the CD before the HDD, then yes you need to change it so it is (like you did). If you want to boot another drive, you would just have to set the BIOS so that drive is before the other drives in the boot order. Or some BIOSes offer the option on start up where if you press F10/F12 or a key like that, you get a boot menu where you can choose which drive to boot for that time only. Anyway, glad to hear your installation went OK this time; cheers and have fun with your new Ubuntu install.

---

### Post by captkirk on 2008-12-14
> **caljohnsmith said:**
> Here's some good information on Grub:

[http://www.users.bigpond.net.au/hermanzone/p15.htm](http://www.users.bigpond.net.au/hermanzone/p15.htm)

About changing your BIOS to boot the CD, if your BIOS isn't all ready set to boot the CD before the HDD, then yes you need to change it so it is (like you did). If you want to boot another drive, you would just have to set the BIOS so that drive is before the other drives in the boot order. Or some BIOSes offer the option on start up where if you press F10/F12 or a key like that, you get a boot menu where you can choose which drive to boot for that time only. Anyway, glad to hear your installation went OK this time; cheers and have fun with your new Ubuntu install.

Thanks on both counts.  I may not have made it clear in my post, but I did the opposite of what you are saying (which is why I asked).  I had to set to boot from the hard drive, not the cd, which makes no sense.  The good news is I am back up and running, and everything seems to work much better.

---

