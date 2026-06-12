---
title: "Problems booting from USB on Cebop Laptop"
date: 2007-10-30
forum: Hardware &amp; Laptops
---

### Post by Hexxagon on 2007-10-30
Hi.

I have a Cebop Top 900 Laptop.
On the internal Drive is WinXP, and on a USB-Drive is Linux.

Now... I want to boot up Ubuntu from that USB-Drive, but that only works if I remove the internal drive. I have set up the boot priorities right, but as soon as an internal hard drive is present, it doesn't boot from USB. Even if I remove the internal drive from the boot list.

Of course, I don't want to remove my internal drive every time I want to boot up Ubuntu on my Laptop... any ideas??

---

### Post by scherry on 2008-03-03
I'm a complete noob with Linux, so take my reply accordingly.  I have an IBM Thinkpad with WinXP on the internal drive that I was unable to boot into Ubuntu 7.10 using a USB external drive without disconnecting the internal drive until I tried this:
I made sure that the USB drive had at least one partition that was formatted so that WinXP would recognize it.  I then booted into WinXP and it recognized the presence of the USB drive.  Then I selected "Restart" from the start menu, got into the BIOS, and the BIOS recognized the USB drive as a hard drive and allowed me to select it as the first boot device.  This only works for me if I boot into WinXP first so that the BIOS knows that there's another hard drive there.
Good Luck.

---

