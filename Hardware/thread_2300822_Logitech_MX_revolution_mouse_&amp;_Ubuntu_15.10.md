---
title: "Logitech MX revolution mouse &amp; Ubuntu 15.10"
date: 2015-10-28
forum: Hardware
---

### Post by a_m on 2015-10-28
Hallo,
my Logitech MX revolution bluetooth mouse has worked fine for many years.... until two days ago when I upgraded from 15.04 to 15.10. Now it simply does not work anymore. I've just installed the new kernel 4.2.5 but it didn't help (it does not work even if I boot with the old kernel 3.19, with which it was working before the upgrade). 
Is there anybody out there who can help me understanding how to make it work again?
 Thanks.

---

### Post by Vladlenin5000 on 2015-10-28
Perhaps you need to delete the device and pair it again. Have you tried that already?

---

### Post by a_m on 2015-10-28
Yes, that was the first thing I tried... no success :( 
Thank you.

---

### Post by TheOuch on 2015-11-03
> **a_m said:**
> Hallo,
my Logitech MX revolution bluetooth mouse has worked fine for many years.... until two days ago when I upgraded from 15.04 to 15.10. Now it simply does not work anymore. I've just installed the new kernel 4.2.5 but it didn't help (it does not work even if I boot with the old kernel 3.19, with which it was working before the upgrade). 
Is there anybody out there who can help me understanding how to make it work again?
 Thanks.

I just fixed this last night.  Here's what I found on a french site:

Edit /lib/udev/rules.d/97-hid2hci.rules

Change this line:

```
KERNEL=="hiddev*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[345abce]|c71[3bc]", \
  RUN+="hid2hci --method=logitech-hid --devpath=%p"

```
to be this (Change hiddev* to hidraw*):

```
KERNEL=="hidraw*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[345abce]|c71[3bc]", \
  RUN+="hid2hci --method=logitech-hid --devpath=%p"

```

---

