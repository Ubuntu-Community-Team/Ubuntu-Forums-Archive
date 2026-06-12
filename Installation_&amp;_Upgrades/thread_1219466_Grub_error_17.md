---
title: "Grub error 17"
date: 2009-07-21
forum: Installation &amp; Upgrades
---

### Post by Isoas on 2009-07-21
Ok so I'm brand new to the linux scene and I tried out Ubuntu 9.04 with a dual boot to my Vista. I had some problems with Ubuntu recognizing my nvidia drivers and decided to get rid of Ubuntu and try Linux Mint. So while in Vista, I deleted the partition containing Ubuntu. Then, went on to make the cd for Mint. When I restarted the computer I got the error message:
 
Grub Loading stage 1.5
Grub loading, please wait
Error 17
 
then it just stays at that screen. 
 
Any help would be greatly appreciated.
 
Thanks in advance.

---

### Post by asqn34 on 2009-07-21
hello Isoas
I found those link below when my grub was giving me some error.
Also on the grub website there is a list of common error code explain.
Basicaly error 17 mean that grub cannot reconnise what type of system file it has to mount

[http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/9398-solving-boot-problems-grub-2nd-edition.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/9398-solving-boot-problems-grub-2nd-edition.html)

[http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_toc.html](http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_toc.html)

Hope it help

---

### Post by oldfred on 2009-07-21
I believe you deleted grub from everything but the mbr when you deleted Ubuntu. The mbr points to /boot/grub to get the stage 1.5 etc & menu.lst files. If you deleted Ubuntu you also deleted the boot directory.

Go ahead and install mint and it should create all new boot/grub files and rewrite the mbr to point to the new location of the /boot/grub files. Other choice is to use the windows disk to repair the mbr - fixdisk/fixboot.

I have been using Ubuntu for 2 or 3 years and while having some issues with the nvidia drivers over the time I am running both the 32 bit from an upgrade (this I believe is where issues were created) and 64 bit from a clean install without any problems at all.

---

### Post by presence1960 on 2009-07-21
do you want to keep Vista and install Mint? Then boot from the Mint Live CD and install Mint. When you get to the screen attached below click the advanced tab and choose to install GRUB to sda (if you only have 1 hard disk). This will put Mint's GRUB on MBR and you will then be able to boot Mint & Vista after the install. There is no need to restore Vista to MBR unless you are going to make it a Vista only machine. You may have to edit menu.lst to get Vista to boot but that should be no problem. Don't restore Vista to MBR if you are going to dual boot because Mint will only overwrite that when installed. It is an unnecessary step unless like I said you want a Vista only machine.

The reason you are getting that GRUB error is you installed GRUB to MBR when you installed Ubuntu. When you removed Ubuntu GRUB remains on the MBR. There is no need to restore Vista bootloader to MBR because when you install Mint it is going to overwrite that anyway. So that is just a wasted exercise. Boot the Mint Live CD and install it. Your vista partition should be fine unless you delete or format it during the install.

---

### Post by presence1960 on 2009-07-21
ooops for got the attachment. this is from Ubuntu but Mint has the same screen:

---

### Post by The Thug on 2009-07-23
I had the same error last night. 

My HDD was partitioned into 3 drives, viz XP OS, XP Data & Ubuntu

I used GParted to delete the XP Data partition and increase the Ubuntu partition. After rebooting, Grub had the Error 17 message.

I solved it by re-installing Ubuntu onto a smaller partition which then re-installed Grub which in turn recognised my other OS's. All I have to do now is remove the "new ubuntu os" entries from Grub and delete the "new os" and re-size my exisiting partition back to what it was.

The error was caused I think by "moving" the whole Ubuntu partition to the left which obviously corrupted the Grub bootloader.

---

### Post by eng.reem on 2009-07-23
i have the same error,but i had created new partition table and lost all my data ,when i used testdisk to recover the lost partitions with ubuntu live cd , i got grub error 17 at stage 1.5 ,how can i fix that plz ?

---

### Post by Isoas on 2009-07-30
thanks for all the help, i figured it out!

---

### Post by rokky on 2010-12-02
One other possible cause for the Error 17 I just discovered:  my PC was trying to boot off a flash drive I left in the USB port which was not bootable (data only). Whew - thought I had to go through all that recovery/re-install pain when all I needed was to pull out the flash drive, and reboot  ;)

HTH

---

