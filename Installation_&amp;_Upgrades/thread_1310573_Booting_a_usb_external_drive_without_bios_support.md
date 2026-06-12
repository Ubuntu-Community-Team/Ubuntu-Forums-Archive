---
title: "Booting a usb external drive without bios support"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by rodSD on 2009-11-01
This is my first post so be easy. I just like to share you my experience.

I wanted to boot a usb external drive. I realized, however, that my bios can't support usb booting.


The background:

I was able to boot from the cd so I installed Ubuntu 9.04 to my usb drive. I also have 3 internal hard drives where one of them has Ubuntu 8.10 installed. The Ubuntu 8.10 is installed on the second hard drive on an extended partition so (hd1,4). My usb external drive is I believe to be sdd1.

How I made it work (might look like a hack):

1.) I copied the kernel and the initrd from the usb drive (under /boot) to my internal hard drive /boot folder. So I copied the following files: vmlinuz-2.6.28-11-generic  and initrd.img-2.6.28-11-generic

2.) I then modified my menu.lst from my internal drive (located at /boot/grub) adding this at the end of the file:

title Ubuntu 9.04 USB pink
root (hd1,4)
kernel    /boot/vmlinuz-2.6.28-11-generic root=/dev/sdd1
initrd    /boot/initrd.img-2.6.28-11-generic
boot

3.) In a terminal I issued this command: update-grub.

4.) Reboot.

It seems to work and seems easy. I obviously don't know why it works. LOL!

Hope this helps. I've been searching for this awhile, but I can't find answers that I like so I experimented on my own.

rod

---

