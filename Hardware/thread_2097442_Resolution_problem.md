---
title: "Resolution problem"
date: 2012-12-23
forum: Hardware
---

### Post by guber90 on 2012-12-23
Hi guys, sry cus of bad english but I think u will get my point :).

I installed ubuntu on my PC, after installing I saw that my resolution is too low, it was only suported up to 1024x768 and my LCD 17'' monitor was detected as CRT, so I tryed to google problem, spent some time on it tryed few tutorials and made a LOT bigger disaster, now my maximum and only resolution now is 640x480.

I have nvidia 9500 GT graphic card, and ubuntu 12.10, my processor is 64 bit.

Also I get this error at starting my ubuntu (after login):

[IMG]http://img803.imageshack.us/img803/3309/screenshotfrom201212231.png[/IMG]

I'm ubuntu beginer so pls try to explain me stuffs step by step :D.

---

### Post by Pjotr123 on 2012-12-23
What kind of monitor do you have? Apparently it's being recognized as CRT, while being an LCD. This might mean hardware trouble, more specifically a damaged monitor (garbled EDID).

---

### Post by guber90 on 2012-12-23
> **Pjotr123 said:**
> What kind of monitor do you have? Apparently it's being recognized as CRT, while being an LCD. This might mean hardware trouble, more specifically a damaged monitor (garbled EDID).

For sure that is not problem on win7 everything is working nice.

---

### Post by Pjotr123 on 2012-12-23
What happens when you install the restricted driver for your video card? 

Start with "current", and if that one doesn't yield good result, try current-updates or even experimental:
[https://sites.google.com/site/easylinuxtipsproject/first#TOC-Make-sure-all-hardware-is-working-properly-and-install-missing-drivers](https://sites.google.com/site/easylinuxtipsproject/first#TOC-Make-sure-all-hardware-is-working-properly-and-install-missing-drivers)

---

### Post by guber90 on 2012-12-23
> **Pjotr123 said:**
> What happens when you install the restricted driver for your video card? 

Start with "current", and if that one doesn't yield good result, try current-updates or even experimental:
[https://sites.google.com/site/easylinuxtipsproject/first#TOC-Make-sure-all-hardware-is-working-properly-and-install-missing-drivers](https://sites.google.com/site/easylinuxtipsproject/first#TOC-Make-sure-all-hardware-is-working-properly-and-install-missing-drivers)

Sry but I'm noobish about ubuntu so could you explain me your post a bit more. What is restricted driver for my video card. Is it this:
[IMG]http://img707.imageshack.us/img707/3309/screenshotfrom201212231.png[/IMG]

Cus I tryed every single one of them and no help.

---

### Post by Pjotr123 on 2012-12-23
Maybe this can help:
[https://sites.google.com/site/easylinuxtipsproject/display#TOC-Wrong-resolution:-Nvidia-card](https://sites.google.com/site/easylinuxtipsproject/display#TOC-Wrong-resolution:-Nvidia-card)
(item 2.2)

---

### Post by guber90 on 2012-12-23
> **Pjotr123 said:**
> Maybe this can help:
[https://sites.google.com/site/easylinuxtipsproject/display#TOC-Wrong-resolution:-Nvidia-card](https://sites.google.com/site/easylinuxtipsproject/display#TOC-Wrong-resolution:-Nvidia-card)
(item 2.2)

Like I already told I can only go up to 640x480, don't see how could this help.

---

### Post by Pjotr123 on 2012-12-23
Try xrandr:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

