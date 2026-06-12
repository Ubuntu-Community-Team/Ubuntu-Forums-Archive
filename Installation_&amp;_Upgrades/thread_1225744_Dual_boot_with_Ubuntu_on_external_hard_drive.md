---
title: "Dual boot with Ubuntu on external hard drive"
date: 2009-07-28
forum: Installation &amp; Upgrades
---

### Post by Conceptz on 2009-07-28
Hello all,

My goal was to run Ubuntu when the external hard drive is plugged into my laptop and run Vista when it is not plugged in.

When I installed ubuntu on my external HD, Grub overwrites my MBR. So when I try to run Vista without my external HD plugged in, I get a Grub error (#17 I believe). I read this thread ([COLOR="Red"][http://ubuntuforums.org/showthread.php?p=3995006#post3995006]("http://ubuntuforums.org/showthread.php?p=3995006#post3995006")[/COLOR]) and realize a simple fix would be to change the boot order in my BIOS to boot USB first then the internal HD. The laptop is from work and unfortunately I don't have access to changing the BIOS settings.

So is there any other way I can boot Ubuntu off my external hard drive without changing the boot order?

Thank you for reading:wink:

---

### Post by stlsaint on 2009-07-29
if you have the ability to boot from a cd...than you can just use a recoverycd called "DaRT for vista" you should be able to re-install your mbr from the cd and make vista the default bootloader! or option 2...
in ubuntu try using a program called easybcd...this is a program that enables you to set which partitions or drives you will have the option to boot from without changing bootorder but in your case that will be your ext-dd. tho it is a windows program so you will have to install thru wine but all you have to do from there is go to your settings and choose to re-install vista bootloader! try these and if nothing works we can try more options!!!

---

### Post by utnubuuser on 2009-07-29
Get permission from your employer to access BIOS?

---

### Post by Conceptz on 2009-07-29
> **stlsaint said:**
> if you have the ability to boot from a cd...than you can just use a recoverycd called "DaRT for vista" you should be able to re-install your mbr from the cd and make vista the default bootloader! or option 2...
in ubuntu try using a program called easybcd...this is a program that enables you to set which partitions or drives you will have the option to boot from without changing bootorder but in your case that will be your ext-dd. tho it is a windows program so you will have to install thru wine but all you have to do from there is go to your settings and choose to re-install vista bootloader! try these and if nothing works we can try more options!!!

I installed EasyBCD on Vista and added Ubuntu into the the boot entries. At startup Windows Boot Manager shows up, allowing me to select Vista or Ubuntu. When I select Ubuntu it goes into Grub prompt. Vista works fine though.

I followed methods 1 & 3 in this guide ([[COLOR="Red"]Manually boot into a Linux OS[/COLOR]]("https://help.ubuntu.com/community/GrubHowto#Manually boot into a Linux OS")) however it doesn't seem to work. Bellow are the error messages.

**Method #1**
grub>  root  (hd1,0)
//Filesystem type is ext2fs, partition type0x83

grub>  chainloader +1
//Error 1: Filename must be either an absolte pathname or blocklist

grub>  boot
//

**Method #3**
grub>  configfile  (hd1,2)/boot/grub/menu.lst 
//Error2: Bad file or directory type

---

### Post by Conceptz on 2009-07-30
bump:-\"

---

### Post by i.r.id10t on 2009-07-30
Fall back to what we did when all we had was lilo.

Install to external, write boot record to your / partition instead of the MBR.  Assume your / is /dev/sda1.

Then peel off your boot record from that with dd and put it in a file

dd if=/dev/sda1 of=/linuxbootrecord bs=512 count=1

Then put that linuxbootrecord file where Vista can see it.  Then edit vista's boot.ini to reference it.

Look up the older howto's for dual booting NT/2k with lilo and follow that process.

---

