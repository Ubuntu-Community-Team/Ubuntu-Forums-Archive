---
title: "Question about dd issue"
date: 2012-11-14
forum: Hardware
---

### Post by sktd on 2012-11-14
Admittedly, this question is probably more related to another distro and may not apply to Ubuntu (which I also use) but that distro's website is down and I imagine that someone here will likely know the correct answer.

I use dd to clone USB thumb drives that are bootable (meaning I have a bootable copy of a Linux distro on them). These source USB's are not LiveUSB installations; they are just regular Linux installations but to a USB drive. When I clone one of these, I use a target USB drive of the exact same size, model, and manufacturer, just to try and eliminate problems. But one thing I've noticed is that with some distros (like CentOS, I think), one issue still comes up. USB drives have a serial number burned into them and with some distros, three of the files utilized during bootup have entries in them that describe the drive being used and that description includes the drive's serial number. Thus, if you don't edit these three files and change the old serial number to the current serial number of the clone, Linux won't boot up.

My problem is that I don't remember which three files include this information or where those files are located within the Linux filesystem. Can anyone provide me with that information?

---

### Post by SlugSlug on 2012-11-14
pretty sure you only have to edit one file

/etc/fstab

sudo blkid

will show you the UUID's of each device

---

### Post by sktd on 2012-11-14
I think one of the other two files is /etc/grub.conf but I don't remember what the third file was.

---

