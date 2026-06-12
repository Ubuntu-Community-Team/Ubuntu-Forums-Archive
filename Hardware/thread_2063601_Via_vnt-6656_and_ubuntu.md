---
title: "Via vnt-6656 and ubuntu"
date: 2012-09-27
forum: Hardware
---

### Post by pakonan on 2012-09-27
Hello. I have bought a mini-pc wich has an internal wireless card. In the output of the lsusb command I can see that the wireless card is a via vnt_6656. But there are any module loaded for this card ant it does not appear in the iwconfig or ifconfig output. Has anyone this card working?
I have found this page: [http://cateee.net/lkddb/web-lkddb/VT6656.html](http://cateee.net/lkddb/web-lkddb/VT6656.html)
If I try to manual load the module I get an error saying that the module is not avaliable
[]("http://cateee.net/lkddb/web-lkddb/VT6656.html")

---

### Post by Sonsum on 2012-09-27
Instructions for Debian (which should be very similar to Ubuntu) are located [here]("http://wiki.debian.org/vt665x")

Perhaps you are missing the ```
firmware-linux-nonfree
``` package?

---

### Post by pakonan on 2012-09-28
Hello
I have already installed this package, but it does not work. I still ca not load the module for the wireless card


Thanks for your help

---

### Post by pakonan on 2012-10-02
I have try the old ubuntu 11.10 with the same hardware. It detects the network card and I can list the ssid in the area. The problem, with this ubuntu version, is that I can not join to my network (wpa2-psk cypher: aes 128 ). I have check that the password is right.

---

