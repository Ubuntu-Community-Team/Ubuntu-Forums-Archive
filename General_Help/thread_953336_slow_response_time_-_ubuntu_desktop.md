---
title: "slow response time - ubuntu desktop"
date: 2008-10-20
forum: General Help
---

### Post by davidbd on 2008-10-20
Hello,

I installed ubuntu using wubi on my local disk and it works fine but there is a general slow response time.

My PC configuration is low-end : pentium-3 celleron 800MHz 512MB mee 40G Disk

What is your suggestion ?

Maybe the gnome desktop manager is too heavy for that PC ?

Regards,
David.

---

### Post by renzokuken on 2008-10-20
Firstly, do you have the correct grafix drivers installed? (what is your grafix card/chipset?)

Secondly, if you want a lighter desktop manager, try either XFCE (Xubuntu), Openbox or Fluxbox (all available in the repos)

---

### Post by davidbd on 2008-10-20
I am using the on-board graphic chip-set. 
How can I check the hardware and which driver is installed? 
David

---

### Post by renzokuken on 2008-10-20
the output of ```
lspci
``` should tell you waht your chipset is.....and the output of ```
cat /etc/X11/xorg.conf
``` will tell you what driver it is using. Just post the output here if you are unsure

---

### Post by davidbd on 2008-10-20
let say it the graphic chipset/card is wrong how can I setup it to a new one and were I can find the drivers ?

---

### Post by renzokuken on 2008-10-20
well if its using the wrong driver you can usually reconfigure xorg to use the proper driver by running and following this wizard ```
sudo dpkg-reconfigure xserver-xorg
``` .....or alternatively by editing the xorg.conf manually. but to do either of these you will still need to know what your chipset is anyway so you can choose the correct driver.

---

### Post by bookfly on 2008-10-21
may be i can

---

