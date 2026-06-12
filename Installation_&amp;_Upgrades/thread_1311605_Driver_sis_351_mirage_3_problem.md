---
title: "Driver sis 351 mirage 3 problem"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by Ravenath on 2009-11-02
Hi Everyone:

I have a laptop with sis 351 mirage 3 igp graphic card. I have installed ubuntu 9.10 but my best resolution is 1024 x 768. I had windows xp before, and I could do:

1-have a resolution of 1280 x 800
2-autodetect my 40' tv, with 1280 x 720

Have you any help with this problem?

Thanks to all of you for your answers and you time.

---

### Post by cariboo on 2009-11-02
Have a look at this [page]("http://www.sis.com/support/support_faqs_16.htm"), it probably hasn't been updated in a looong time. You will probably have to set up modaliases in /etc/X11/xorg.conf

Have a look at this [post]("http://ubuntuforums.org/showpost.php?p=6116605&postcount=12"), it may help.

---

### Post by Ravenath on 2009-11-02
Thanks! I'll see if this works for me. I'll tell you with my next post.

---

### Post by tormod on 2009-11-02
Please run: ubuntu-bug xserver-xorg-video-sis

---

