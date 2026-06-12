---
title: "Screen rolls during alt installer install"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by castufari on 2008-12-24
I had 8.10 running on here. I have to encrypt everything except boot so I grabbed the 8.10 alt installer CD. Insert it, boot. Hit enter for install and boom, the screen starts rolling like an old TV.

It's a Dell D810 with 2gb of memory. 8.10 installed just fine but the 8.10 alt installer is being a PITA.

---

### Post by lemming465 on 2008-12-28
Try booting the installer with a *vga=* option to choose a different display mode, since it's getting the default choice wrong.  You can find some likely numbers [here in section 5.3]("http://www.tldp.org/HOWTO/Framebuffer-HOWTO-5.html").  Maybe **vga=0x163**

---

