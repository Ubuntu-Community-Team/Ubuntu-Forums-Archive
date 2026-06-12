---
title: "Creating a Live USB destroyed a dual-boot computer!"
date: 2009-04-08
forum: Installation &amp; Upgrades
---

### Post by DashW on 2009-04-08
BEFORE: A computer able to dual boot into Windows 7 and Windows XP, using the Windows 7 Boot-Loader.

THEN: Attempted to install gOS Linux (which is based on ubuntu 8.04) onto a 16GB USB pen drive using the standard gOS/ubuntu installer.
Left the advanced settings untouched, and accidentally installed the GRUB boot loader onto the boot drive!!

AFTER: Unable to boot into Windows XP, Windows 7 or the Live USB!!!

THEN: Used the Windows 7 setup disk to fix the Windows 7 boot loader... sort of...
Visited pendrivelinux.com and followed the long-winded instructions to create a gOS Live USB. All steps completed successfully, but still unable to boot.

NOW: Fully able to boot into Windows 7, but no program can identify the XP installation, even though the file structure of that partition is still intact.
Attempting to boot into the Live USB produces "Error 17".

Help!

---

### Post by snowpine on 2009-04-08
Hi DashW,

When you get to the last step of the installer, you need to click Advanced Options and install Grub to the correct device, the USB drive (for example, /dev/sdb, though it depends on your computer).

A better option is to use an application called Unetbootin, or the "Create a USB Startup Disk" option in Ubuntu 8.10. This type of "Live" install has many advantages over a "standard" install on a USB stick, like you attempted, mainly that it uses less space on the drive and preserves its lifespan.

Sorry but I am not a windows user and can't help you repair the XP/7 dual boot. :(

---

### Post by DashW on 2009-04-08
> A better option is to use an application called Unetbootin, or the "Create a USB Startup Disk" option in Ubuntu 8.10. This type of "Live" install has many advantages over a "standard" install on a USB stick, like you attempted, mainly that it uses less space on the drive and preserves its lifespan.


Thanks for the suggestion, but I've tried using uNetbootin to create a Live USB like that. The trouble is, the resulting drive doesn't store any changes like updates or preferences, and these things are very important to me. I'm afraid it's not what I'm looking for.

---

### Post by snowpine on 2009-04-08
> **DashW said:**
> Thanks for the suggestion, but I've tried using uNetbootin to create a Live USB like that. The trouble is, the resulting drive doesn't store any changes like updates or preferences, and these things are very important to me. I'm afraid it's not what I'm looking for.

Live USB Install (Unetbootin)=Copies the Live CD .iso to a bootable USB drive. Does not store any installed applications, documents, or settings.
Persistent USB Install (Pendrivelinux or Ubuntu USB creator)=Like a Live USB, except it also allows you to save your changes.
Full Install (The normal installer, like what you did)=Uncompresses the .iso and does a fully persistent, hard drive type of install. 

Hope that clears up the terminology so you can find an appropriate tutorial for your needs. I personally have had good luck with the full install onto a USB drive, though you need to click Advanced Options as I mentioned above. (Also be aware this type of install requires twice as much space on the drive and will wear it out quicker, especially if you use a swap partition.) If you are in doubt, just disconnect the hard drive before getting started, that way there is no risk of messing up the bootloader. I have an old computer with no hard drive that I use for exactly this purpose. Good luck!

Maybe if you want to talk more about your goals and needs I can give you some more general advice to achieve them.

---

### Post by DashW on 2009-04-08
AAAARGH! The Windows XP "Recovery Console" gives me the Blue Screen Of Death!!!!

---

### Post by DashW on 2009-04-08
I have performed a full install of gOS on the USB device, but whenever I try to boot from it, the GRUB bootloader gives me the error message "Cannot mount selected partition".

---

### Post by upchucky on 2009-04-08
dont panic,its all still there, just need to do a few things

boot the pc using the ubuntu live cd then

download this

[http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055) 

then do this in a terminal.

```
sudo bash ~/Desktop/boot_info_script*.sh

```

post the results of the file here so we know the drive geometry.


also download this and create the supergrub repair utility cd,

Supergrub

Get Supergrub to set up/repair Grub here:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

after you have downloaded and created the supergrub disk boot from it then use it to fix grub.

you must read the instructions carefully and understand them, google what you do not understand. You will not hurt anything with this but can get very confused if you do not understand what it does.

there are people here that can tell you exactly what to do to fix your system based on the info the above file reports, however supergrub will also fix it, as long as you understand what it does and how it works.

there is a utility on the win install cd that repairs the win mbr called fixmbr. use it only if you are booting windows from its own drive
as a standalone os. (no ubuntu on the drive)

---

### Post by rahul_bhise on 2009-04-08
go [hear]("http://users.bigpond.net.au/hermanzone/p18.htm") and [hear]("http://users.bigpond.net.au/hermanzone/p15.htm") and search for your answer or you could reed the full [website]("http://users.bigpond.net.au/hermanzone")

---

### Post by snowpine on 2009-04-08
The problem basically is the 8.04 installer is designed to install grub on a hard drive, not a USB drive. A lot of users demanded a better USB installer, so in 8.10 and newer, they bundled the USB Creator utility, which is similar to the pendrivelinux approach. Compared to the method you are trying, it would save space on the drive, preserve its lifespan, and bypass the grub problem.

Anyway, it sounds like you are on the right track, but your grub is broken. Do you see a grub menu at boot up, before you get to the error message? If so, you can press 'e' to edit the boot command. I can't really explain in a short message how grub works, but for example if it says 'hd(1,1)' (second drive) try changing it to 'hd(0,1)' (first drive). I really cannot be more specific because I don't have any experience with gOS. In the past, I have trouble-shot this kind of problem by looking for good tutorials on fixing a broken grub (see the posts above mine). Once you find a fix that works, you can make it permanent by editing your /boot/grub/menu.lst text file. Good luck!

---

### Post by upchucky on 2009-04-09
i had to go back and edit my post, the site i linked supergrub to is broken, i changed it to the supergrub site instead

---

### Post by DashW on 2009-04-10
Thanks for all your help guys, problems solved.

With the Windows PC: Reinstalled Windows 7!
(It's only been around a few months, so no big loss. This completely restored the bootloader)

With the USB Disk: Installed from the CD, changed the GRUB root
(from hd2 to hd0)

Now it's all working great!

Just one small question: How do you remove a swap file/partition? I have a feeling this might wear out my USB...

---

