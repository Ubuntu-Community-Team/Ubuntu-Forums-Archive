---
title: "Compatibility with HP PAVILLION model # G61-424CA"
date: 2010-10-21
forum: Hardware
---

### Post by sagewerewolf on 2010-10-21
I had HP dv2000 series laptop, and once tried Ubuntu 10.04 on it.
I adored it really, made windows seem... meh.

Anyways, to my point. I couldn't get wireless working on that laptop and got a desktop for my studies, however I'm considering that laptop, and I really want to install Ubuntu on it, since it's just a "for me" machine.

Anyone know if HP still uses Broadcom wireless chipsets, and if that "linux driver" (which did not work for me at the time) is compatible with the new release of Ubuntu? (10.10)

Many thanks!

---

### Post by desnaike on 2010-10-21
I have the g61-429wm atheros ar9285 wifi and it works for U/K/Xubuntu 10.04,10.10 out of the box. I would suggest the first thing to do after installing the os is install the video driver before updates or anything else.

---

### Post by CompShrink on 2010-10-23
Short answer: No, it's not well supported. Some people can get it working, some can't.

You can take a look at: [https://bugs.launchpad.net/linux/+bug/518818](https://bugs.launchpad.net/linux/+bug/518818)

It works for some out of the box on 10.10. It works after compiling compat-wireless-2010-09-12 for others (myself included, install build-essential and then see instructions [https://bugs.launchpad.net/linux/+bug/518818/comments/81](https://bugs.launchpad.net/linux/+bug/518818/comments/81)). Some people report that recompile not working, and nothing else they tried working. 

For a while I used a usb wireless card. You can also spend around $30-50 to get a replacement internal wireless card.

---

