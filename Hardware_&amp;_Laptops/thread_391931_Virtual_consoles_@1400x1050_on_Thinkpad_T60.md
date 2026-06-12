---
title: "Virtual consoles @1400x1050 on Thinkpad T60"
date: 2007-03-23
forum: Hardware &amp; Laptops
---

### Post by lamborghiniwang on 2007-03-23
I'm running ubuntu Edgy on my Thinkpad T60 with a 14" SXGA+ display, and I'm having a problem on enable framebuffer @1400x1050 . When I try to set the kernel option "vga=835"(also 836 and 837) in grub, the start-up messages display correctly @1400x1050(I've disabled the boot splash), but if I try to switch back to virtual consoles via Ctrl-Alt-F1 after gdm comes up, I see a few columns of artifacts and all the texts is shaking(sort of). It only affects the virtual console, gnome displays well and with the ATI fglrx driver (I tried both 8.29 and 8.34)
The virtual console works fine when I change the kernel option into "vga=791"(1024x768), but I just want to know if there is a way to make it works @1400x1050.
Any suggestion?
I forgot to mention, the video card is an ATI Mobillity X1400 (128MB)

---

### Post by lamborghiniwang on 2007-04-01
OK, I think I kinda solved the problem. It turns out that I need to turn off the "LCD HV expansion" in BIOS when setting the resolution of virtual consoles into 1400x1050. This means the grub booting screen won't cover the entire screen.

---

### Post by dan-arwed on 2007-06-04
Hi lamborghiniwang,

thank you so much for your post... I had similar problems with edgy eft (6.10) on an IBM Z61m 
Laptop, ATi Radeon x1400 graphics card. A console login or session was not possible (weird and fuzzy screen as well).

In Bios, the "LCD HV Option" was switched on by default, too. Unfortumately switching it off didn't
help. But setting vga=791 solved the problem at first glance, now i am at least able to use 1024x760 which is sufficient for me.

Best regards,

Dan

---

