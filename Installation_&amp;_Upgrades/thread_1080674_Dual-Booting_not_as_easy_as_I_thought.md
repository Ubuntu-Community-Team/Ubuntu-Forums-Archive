---
title: "Dual-Booting not as easy as I thought"
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by abyrne on 2009-02-25
HI,

I'm not new to Ubuntu itself because I've ran it several times on  VirtualBox. Now I'm ready to install it on my portable drive so I can boot it up if, I mean, when VISTA GOES BAD. So first I tried Wubi, which screwed with Vista's bootloader by adding Ubuntu as an entry, which I don't want. I just want to be able run Vista, and when it goes belly up, be able to go into my BIOS, select Boot from USB, and boot Ubuntu. Is it possible to do that and is it possible for Ubuntu to just simply install onto a partition on my portable HD without touching my Windows Drive. Please Reply. Thanks in advance.
):P

---

### Post by caljohnsmith on 2009-02-25
Sure, when you install Ubuntu to your USB drive, click the "advanced" button near the end of the installation process, and there you can specify to have Grub installed to "/dev/sdb" or whichever is the USB drive. Then when you change your BIOS to boot the USB drive, you should be able to boot Ubuntu.

---

### Post by abyrne on 2009-02-25
Thanks for the advice. It all works perfectly now.:KS

---

