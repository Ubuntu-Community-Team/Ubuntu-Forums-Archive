---
title: "SiS 672 Display"
date: 2012-06-24
forum: Hardware
---

### Post by yolandre on 2012-06-24
Hi all,
I've been trying to configure a laptop's display driver in order to get a better resolution. According to the manufacturer's spec sheet the laptop is equipped with the Sis M672 display chip, but according to SysInfo it is the SiS 771/671 display chip.
As such I've tried a couple of methods including [https://sites.google.com/site/easylinuxtipsproject/sis](https://sites.google.com/site/easylinuxtipsproject/sis), but all to no avail. Does anyone have advice?

Thanks in advance!

---

### Post by Pjotr123 on 2012-06-24
You might try my how-to again, which I've attempted to clarify and improve:
[https://sites.google.com/site/easylinuxtipsproject/sis](https://sites.google.com/site/easylinuxtipsproject/sis)

If it's really a 671 or 771 chipset (and not a 672), this should work. Note the importance of choosing the right architecture for your system (32 bit or 64 bit).

A complication might be, that your system has become polluted by the previous unsuccesful attempts. In your place, I'd consider a clean reinstallation of Ubuntu, for example like this:
[https://sites.google.com/site/easylinuxtipsproject/reinstallation](https://sites.google.com/site/easylinuxtipsproject/reinstallation)

---

### Post by mzaam on 2012-09-01
try this one
[http://hellbunker.blogspot.com/2011/03/driver-sis-m671-m672-for-upcoming-natty.html](http://hellbunker.blogspot.com/2011/03/driver-sis-m671-m672-for-upcoming-natty.html)
it work for me

---

