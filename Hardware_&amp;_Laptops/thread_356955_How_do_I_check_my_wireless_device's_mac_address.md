---
title: "How do I check my wireless device's mac address"
date: 2007-02-09
forum: Hardware &amp; Laptops
---

### Post by curtis1005 on 2007-02-09
Recently I am following one of the tutorial which I found in this forum to get my wireless working with my ubuntu.
However I am stuck with one of the steps, it requires me to add my wireless device's mac address into /etc/iftab
 
My question is how can I find out the mac address of my wireless device?
 
much appreciated if someone could help me solve this problem
 
P.S my laptop is Asus A4L with SiS usb2.0 wireless device.

---

### Post by gradedcheese on 2007-02-09
Easy: just run 'ifconfig' and look at the HwAddr reported (for your wireless device).  Which one is the wireless?  Run 'iwconfig', it's the one with wireless extensions.

---

