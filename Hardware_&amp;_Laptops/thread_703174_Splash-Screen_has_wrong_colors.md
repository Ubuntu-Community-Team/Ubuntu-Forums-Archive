---
title: "Splash-Screen has wrong colors"
date: 2008-02-21
forum: Hardware &amp; Laptops
---

### Post by nielsk on 2008-02-21
Hi!

I'm using a Libretto L1 with a S3 Savage/IX (the resoultion is 1280x600) and everything worked more or less fine until I upgraded to 7.10.

I got my TTYs to work in full resolution with editing the /etc/initramfs/modules and adding fbcon and vesafb and updating the initrd afterwards (and setting vga=0x404). But when I boot with splash-screen enabled the ubuntu-logo is grey and the text is green. I doubt that these are the right colors.
Any ideas how I get correct colors? It's not really important but would be nice.

---

### Post by nielsk on 2008-02-21
I just noticed that I get the right colors when I do not add vga=0x404 and just stay with 800x600…but that's not a real solution

---

