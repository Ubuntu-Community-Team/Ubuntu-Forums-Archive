---
title: "Can I install Vista to a USB external hd?"
date: 2007-12-28
forum: Hardware &amp; Laptops
---

### Post by Neo40 on 2007-12-28
Hi,

I have a HP laptop with Ubuntu installed. I want to buy  a usb external HD  and I'd like to know if I could install Vista on it? From Grub, it will give me the choice to boot Ubuntu or Vista. How can I do that (if it's possible)?

Thanks

---

### Post by logos34 on 2007-12-28
I believe you'll have to disconnect your lappy's internal drive (i.e. you may even have to unscrew it and slide it out) before vista will install.  Or at the very least set the usb drive as the first boot disk in the BIOS.  For example, you can't install XP on a slave drive until you switch the Bios order. 

Add a vista entry with the requisite [mapping]("http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows") to the bottom of [/boot/grub/menu.lst]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk").

---

