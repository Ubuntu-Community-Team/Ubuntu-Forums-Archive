---
title: "My internets are very slow and I think it's my motherboard"
date: 2007-04-05
forum: Hardware &amp; Laptops
---

### Post by TeeAhr1 on 2007-04-05
My connection has always been the slowest and most fickle in my house (of four machines, three of which are running nearly identical Ubuntu installs).  I have tried things ranging from replacing the cable modem to going ethernet instead of wireless to swapping in different ethernet cards.  Nothing really helps.  Process of elimination has brought me to the assumption that if it's not my ethernet card and it's not the modem and other computers connected here are "faster enough" (sorry for the tortured sentence structure) that it's visible to the naked eye, then it must be...something else.

I don't know how to test this assumption, and I don't know what I could do about it if proven right.  Can anybody help me out?  I don't even know where to start, but I take instruction well.  Thanks.

-p.

EDIT: It's a desktop.

---

### Post by evilghost on 2007-04-06
Have you disabled the ipv6 module from loading?  I noticed that ipv6+ipv4 on an ipv4 network cause all kinds of headaches with sporadic DNS resolution, packet timeout, etc.

---

### Post by TeeAhr1 on 2007-04-06
Hrm.  No.  How do I go about that?  (sorry so long in replying, I posted right before I went to bed)

-p.

---

### Post by evilghost on 2007-04-06
sudo pico /etc/modprobe.d/aliases

Change:
alias net-pf-10 ipv6

To:
alias net-pf-10 off

Save, and reboot.

---

