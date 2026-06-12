---
title: "Ubuntu won't boot off of USB drive on macbook"
date: 2006-12-18
forum: Hardware &amp; Laptops
---

### Post by brucedes on 2006-12-18
I have rEFIt installed on my macbook, and installed ubuntu 6.10 onto my external usb drive.

To install grub I made a 50Mb boot partition on the USB drive, and the install completed properly, without an error. 

rEFIt then shows Linux on the USB drive, but when I select it, all I get is a blank screen with a blinking cursor in the top right corner of the screen.

Any ideas what I have to do to make it boot?

---

### Post by zbittner on 2007-01-15
I have a similar problem. I was able to install 6.10 on my second hard drive in my Mac Pro. I then installed lilo, because GRUB wouldn't install, but when I try booting from it, it says the operating system isn't found. When I go into rEFIt partition manager, only the EFI partition on the first drive, and the Mac OS X partition show up.

I think the problem is that rEFIt doesn't look at the partition table that is created on the second drive. It would be awesome if someone could verify/disprove this.

---

### Post by lordmule on 2007-02-01
just to be clear, did you install using the standard 6.10-desktop or the 6.10-alternate?

The alternate is the one you need to avoid changing the MBR on the macbook pro HDD. This could be the reason why grub failed. I'm going to try it myself, i'll need to grab a 4gb pen drive first.

 me: Macbook Pro 2.0GHz MS+OSX only ---> awful

---

