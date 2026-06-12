---
title: "Slow text console performance"
date: 2009-06-09
forum: Hardware
---

### Post by valavanisalex on 2009-06-09
Hi there,

I have set the vga=0x361 kernel flag on my HP Compaq Presario CQ50 laptop so that everything appears in 1280x800 resolution in text mode.  

Everything appears correctly when I switch to a text terminal (CTRL+ALT+F1) but the refresh rate is extremely slow.  For example, concatenating a long file to screen takes an extraordinarily long time.  By contrast, everything seems fine when I'm running an X server.

I've put more details in the following bug report but I haven't had any replies:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/297704](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/297704)

Is this just a case of me having crappy hardware or is it some problem with the framebuffer software that can be improved?

Any ideas?

---

