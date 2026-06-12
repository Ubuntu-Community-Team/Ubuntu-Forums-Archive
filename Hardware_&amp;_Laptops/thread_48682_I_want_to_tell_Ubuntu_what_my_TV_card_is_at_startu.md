---
title: "I want to tell Ubuntu what my TV card is at startup"
date: 2005-07-13
forum: Hardware &amp; Laptops
---

### Post by lordgibbness on 2005-07-13
Hi all,

I have been using Ubuntu for a number of weeks now and all seems to be going quite well. I've had a number of issues where I've got a bit stuck, but managed to resolve them in the end.

However, my TV card (Pinnacle PCTV Rave) is not automatically detected by Ubuntu. In order for TV Time to make use of it I have to enter the following commands every time I load Ubuntu:

sudo rmmod bttv
sudo modprobe bttv card=39 tuner=7

Is there any way that I can get this to happen at boot up? Editing one of the /etc files for example?

Thanks in advance. (Using Ubuntu 5.04)

---

### Post by mo_x on 2005-07-13
Add it to the file /etc/modules to load it at boot time. I think you can just add the line:
bttv card=39 tuner=7
See the manual pages modules and modprobe.conf.
My TV card, also PCTV Rave, is automatically detetected in Ubuntu.

Mo X

---

### Post by lordgibbness on 2005-07-13
Thanks very much, that did the job!

I wonder why mine wasn't detected but yours was then? Maybe mine's an older model or something - I've had it for about 5 years now.

---

