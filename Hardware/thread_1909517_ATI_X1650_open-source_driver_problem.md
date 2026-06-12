---
title: "ATI X1650 open-source driver problem"
date: 2012-01-15
forum: Hardware
---

### Post by Fusion10 on 2012-01-15
Hello everybody. I'm new here and a Linux beginner so, after I've installed Ubuntu 11.10 I've encountered the following display problems:

[http://img192.imageshack.us/img192/3836/screenshotat20120113194.png](http://img192.imageshack.us/img192/3836/screenshotat20120113194.png)
[http://img842.imageshack.us/img842/3836/screenshotat20120113194.png](http://img842.imageshack.us/img842/3836/screenshotat20120113194.png)
[http://img829.imageshack.us/img829/4655/screenshotat20120113195.png](http://img829.imageshack.us/img829/4655/screenshotat20120113195.png)

I think it's a driver problem because after a lot of researching i've tried 'Using the framebuffer' tip from the following link:
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

After rebooting, the problem disappeared but it booted into Ubuntu2D and it was working slowly. It was also showing in system info, at graphics tab, something related to software (i don't remember exactly) instead of Gallium 0.4 on ATI RV530. So i had to come back to the original problem, by deleting the content of xorg.conf.

I would really appreciate if somebody could help me. Cheers !

---

### Post by Fusion10 on 2012-01-18
Bump... Nobody can help me?

---

### Post by Fusion10 on 2012-01-20
Bump........

---

### Post by MoreOrLess on 2012-01-20
Try the xorg-edgers ppa to see if the issue has already been fixed upstream.

---

### Post by Fusion10 on 2012-01-21
Thanks for your reply. I've tried it, but i don't think it's been fixed, or I am doing it wrong...

---

