---
title: "Where do I edit"
date: 2009-08-06
forum: Installation &amp; Upgrades
---

### Post by zebraneo on 2009-08-06
Do I change the code in terminal or something else, and if in termanal how can I save it
This is the first time using Linux and changing code thanks



Make the drive persistent
By making the pen-drive installation persistent, you are modifying the installation to allow you to save changes. This will alter the Linux installation so that it does not assume that install media is unwritable. To do this, you must modify syslinux which was created to boot the drive.

   1.Boot your system from your host operating system (something other than off the pen-drive)
   2. Mount the pen-drive
   3.Edit text.cfg from within the syslinux folder by replacing the default live entry with:

default persistent

label persistent

menu label ^Start ubuntu

kernel /casper/vmlinuz

append file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash perssistent --

---

### Post by Katalog on 2009-08-06
I don't see any reason why you would have to use the terminal. You just simply insert the pen drive, mount it, open the syslinux folder and then open up the text.cfg file in your text editor and make the changes in the instructions you listed above. 

In the event that it won't let you modify the text.cfg file due to a lack of priviliges, just hit "Alt+F2" and run "gksu gedit". You'll then be running the text editor in super user mode and you'll be able to open the text.cfg file, make the changes, and save it.

---

### Post by zebraneo on 2009-08-06
> **zebraneo said:**
> Do I change the code in terminal or something else, and if in termanal how can I save it
This is the first time using Linux and changing code thanks



Make the drive persistent
By making the pen-drive installation persistent, you are modifying the installation to allow you to save changes. This will alter the Linux installation so that it does not assume that install media is unwritable. To do this, you must modify syslinux which was created to boot the drive.

   1.Boot your system from your host operating system (something other than off the pen-drive)
   2. Mount the pen-drive
   3.Edit text.cfg from within the syslinux folder by replacing the default live entry with:

default persistent

label persistent

menu label ^Start ubuntu

kernel /casper/vmlinuz

append file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash perssistent --
is the default live entry just on line or is it a few lines

---

