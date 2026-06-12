---
title: "Asus Z92U - 1280x800 console"
date: 2006-08-09
forum: Hardware &amp; Laptops
---

### Post by mongolito404 on 2006-08-09
Hi,

using [vbetest](http://lrmi.sourceforge.net/), I got Ubuntu (6.06) to use 1280x800 in console (text mode and boot splash) on my Asus Z92U. Add vga=31E to your kernel parameter and it should work.

PS: If you use grub, add "vga=0x31E" and the end of the line starting with "# defoptions" (and keep to "#") in /boot/grub/menu.lst. It should looks like
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=31E
```

---

### Post by hugmenot on 2006-09-30
I hope you subscribed to this thread ... [-o< 

What did you do to the number that vbetest spit out? I get 1400x1050 @ 16-bit as max supported res and the code it gives is [328]. How do I enter that into menu.lst. Which number format is it?

---

### Post by hugmenot on 2006-09-30
Aye, I got it:

[QUOTE=http://gentoo-wiki.com/HOWTO_fbsplash]Modes in square brackets are listed in decimal. Add 512 to the mode you need; pass the result (for example 353+512=865) to your kernel using vga=x, either in decimal (vga=865) or in hexadecimal (vga=0x361).[/QUOTE]

---

