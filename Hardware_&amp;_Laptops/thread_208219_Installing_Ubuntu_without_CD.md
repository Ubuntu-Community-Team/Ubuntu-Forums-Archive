---
title: "Installing Ubuntu without CD"
date: 2006-07-03
forum: Hardware &amp; Laptops
---

### Post by Úlof on 2006-07-03
I'm trying to install Ubuntu 6.06 on my old laptop. Only one problem: both the Diskette and CD drives are USB drives, and my computer can't boot from either them.

When I recently installed Windows XP on the computer, the fact that the computer couldn't boot from the CD drive was solved by copying all the files on the install CD to the second partition on my HDD and run the installer from there.

Is there anyway of doing a similar thing with the Ubuntu install CD? I'm hesitant to try it, because not only does it take well over an hour to copy everything to the HDD (USB 1.1 is *slow*), and what's more, I can't start the installer from the CD.

Any help is would be very much appreciated.

---

### Post by Rumo on 2006-07-04
Hmm, can you boot from an usb-stick or is a network-boot possible? There has to be a possibility to install an operating system. No manufacturer can be that stupid.

The only other "easy" way I can think of is to use loadlin - it can boot a linux system from windows (just google for loadlin). After the boot process has finished you can chroot ('chroot /media/cdrom' or something like that) to the usb cdrom drive and start the ubuntu-installer.

---

