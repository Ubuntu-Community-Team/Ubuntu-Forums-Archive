---
title: "Save - when boothing from USB"
date: 2009-08-06
forum: Installation &amp; Upgrades
---

### Post by zebraneo on 2009-08-06
How can I save the changes that I make, when I boot from a USB drive, and is there any way I can install Linux on a external hard drive

---

### Post by running_rabbit07 on 2009-08-06
I believe that when using the USB Startup Disk Creator under the System>Administration menu it allows you to use the rest of the drive for saving files and settings. You may need to boot up via a LiveCD to do this.

---

### Post by zebraneo on 2009-08-06
I did that but it still doesn't save. What should I do to save

---

### Post by metalf8801 on 2009-08-06
here's what you need to do

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


here where I found this stuff 
[http://www.hubbardandhubbard.com/consulting/index.php/tips/39-general/54-creating-a-live-linux-pen-drive-with-unetbootin](http://www.hubbardandhubbard.com/consulting/index.php/tips/39-general/54-creating-a-live-linux-pen-drive-with-unetbootin)


oh and I change it here so it says ubuntu where it said xubuntu in the tutorial

---

### Post by zebraneo on 2009-08-06
> **metalf8801 said:**
> here's what you need to do

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


here where I found this stuff 
[http://www.hubbardandhubbard.com/consulting/index.php/tips/39-general/54-creating-a-live-linux-pen-drive-with-unetbootin](http://www.hubbardandhubbard.com/consulting/index.php/tips/39-general/54-creating-a-live-linux-pen-drive-with-unetbootin)


oh and I change it here so it says ubuntu where it said xubuntu in the tutorial
do I edit it in terminal, or a different program, and if edit it in terminal how do I have it

---

### Post by metalf8801 on 2009-08-06
um take a look at [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/) 
theres a lot there but I know the answer is there somewhere because I did the same thing a year to 2 ago

---

