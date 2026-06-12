---
title: "MIC NOT WORKING :Intel ICH8 Family (Realtek 268 ) - Acer Aspire 4720"
date: 2007-10-22
forum: Hardware &amp; Laptops
---

### Post by pooh14 on 2007-10-22
Hi Guys,

I am having Acer Aspire 4720 Laptop with HDA Intel ICH8 Family (rev 03)(Realtek 268 ) sound card. I finally got my sound working in Gusty and it took me ages to so. My sound did not work at all in Feisty though (no problem in Windows)

Once I have downloaded latest alsa driver, ALSA 1.0.15rc3, and installed it, I had very soft sound in my headphones but not through speaker.  I then added a line to /etc/modprobe.d/alsa-base : options snd-hda-intel model=acer, I got things working to normal except my Mic

Both my internal and external MIC aren't working.

I hope I can get some help to get the MIC working. Thanks.

---

### Post by pooh14 on 2007-10-25
bumb.

any help please?

---

### Post by be4truth on 2007-12-29
Same here. Any solution yet?
Check here as well:
[https://answers.launchpad.net/ubuntu/+question/20970]("https://answers.launchpad.net/ubuntu/+question/20970")

---

