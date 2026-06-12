---
title: "bootloader on floopy or usb drive"
date: 2005-12-24
forum: Installation &amp; Upgrades
---

### Post by windowsfree on 2005-12-24
I want to install Ubunut 5.1 on a laptop that already has windows on it.  I want to put the bootloader (grub or lilo) on a floppy.  Is there an option to do this or do i have to put it in the master boot record.  I think one of the older Mandrake versions allowed you to put it on a floppy diskette.

Thanks!

---

### Post by Herman on 2005-12-24
You can install GRUB boot loader to a floppy disk. I've not tried a USB drive , but maybe. Make sure you have a formatted floppy disk ready, and have you computer's BIOS set up ready to boot from a floppy disk  before beginning your install, (of course), as you will need to re-boot before the install is finished.
To install GRUB to a floppy, choose 'No' when it asks you if you want to install GRUB boot loader to your master boot record. Then it will give you an extra menu asking you where else you want GRUB installed, and you can type : (fd0) on the line there, (with you floppy disk in the drive).

GAG boot loader is another good boot loader to use on a floppy disk, because the GAG boot floppy is easy to reproduce multiple copies of, in case one floppy disk becomes corrupted or damaged. The GAG boot loader can also be re-configured on your GAG floppy and have the changes saved to the floppy disk. That's pretty handy if you re-partition and change things around in your computer sometimes.
It would also be a good idea to have a GAG boot floppy handy in any case, just because you never know when it might come in handy. 
The GAG bootloader needs either GRUB installed on a seperate /boot partition, or Lilo installed on your new Ubuntu partition in order to boot Ubuntu, or else it will only boot Windows. The simplest way to is to install Lilo. You can do that by choosing 'Go Back', rather than 'No' when it asks if you want GRUB installed on your MBR, that will give you the 'Ubuntu Installer Main Menu', where 'Install Lilo Boot Loader' is just one line down. Then you will see the option to install Lilo to your new Ubunu partition.

For more info on those topics and a few others besides, click on my signature link. 
:smile: (Herman)

---

### Post by windowsfree on 2005-12-26
Thanks, I hope to do the install later today......

---

