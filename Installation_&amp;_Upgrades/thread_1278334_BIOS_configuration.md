---
title: "BIOS configuration"
date: 2009-09-29
forum: Installation &amp; Upgrades
---

### Post by jrev on 2009-09-29
Hi all,

I recently configured a USB key in order to install Ubuntu netbook remix on a new computer.
I tried it on my main computer running ubuntu 9.04 and the start is OK 

I then tried it on my new computer which said :
> boot from CD/DVD
disk boot failure
could not find kernel image

The mother card is : Gigabyte GA-MA74GM-S2H

My question is :

Which device should I select in order to boot on the USB key :

the options are : floppy, LS120, hard disk, CDROM, ZIP, USB-FDD, USB-ZIP, USB-CDROM, USB-HDD, legacy lan, Disabled.

I tried LS120, USB-FDD,  USB-HDD without any success 

Could you find why this new computer with so many options cannot boot on a USB key including a proper OS to install ?

Thanks

---

### Post by rreese6 on 2009-09-29
USB-HDD would be my guess

In BIOS Check the state of USB Legacy and change it.

A google search revealed that some owners of the same board
had dead USB ports on new boards...Info mainly from newegg site

---

### Post by jrev on 2009-09-30
In fact, the hard disk had been disconnected !

But this doesn't solve my problem : howto be able to boot on a USB disk with this type of PC ?

The USB-HDD option was no good :P

Here is what you can find in the USB install key :
[http://www.zimagez.com/zimage/capture-disk-navigateurdefichiers0.php](http://www.zimagez.com/zimage/capture-disk-navigateurdefichiers0.php)

Is there anything missing ? for example a linux image ?
But then why does it boot on another PC ? 

Thanks

---

### Post by jrev on 2009-09-30
I tried my USB install key on a third PC with Ubuntu 9.04 and BIOS Award and the boot was OK on the first boot device as **USB-ZIP**

I then tried this option on the reluctant PC which blocked on the boot, after verifying DMI pool data :

> Syslinux 3.53 Debian 2009.03.09 C BIOS copyright. 1994-2007 H. Peter Anvin 
Boot: could not find kernel image : Linux 

I tried to boot on an installation CD and there again the boot went to the HDD

---

### Post by jrev on 2009-10-02
Up please or 
[FONT="Arial Black"][SIZE="7"]
[SIZE="7"]How to fix a bad BIOS ? [/SIZE][/SIZE][/FONT]

---

### Post by rreese6 on 2009-10-04
ok think about this...if the CD does not boot and it defaults to HD for booting. Three possible issues here.
1. CD-ROM Drive is defective or not connected correctly (Unlikely)
2. Bios not set up to Boot CD-ROM first, or
3. CD-ROM does not have boot-able media. Like when someone burns a DATA CD and only transfers the ISO File to the disk instead of Burning a CD from an ISO Image.

The view that it would appear that your USB began to boot then Could not
find a file was unusual. but you say the USB works on other machines...just not this one.....almost like after the boot starts, it forgets where is was reading.......does that seem about right?

---

### Post by jrev on 2009-10-14
The solution was there :
the install booting key is considered as a Hard disk

So on my phoenix award BIOS :

1   insert your USB key before entering the BIOS 
2   Reboot and enter the BIOS 
3   select <Advanced boot features>
4   select <HD boot priority>, select your key and bring it to line 1

That is the trick...
Thanks for your answers

---

