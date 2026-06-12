---
title: "WiFi on ThinkPad X220 with 11.04"
date: 2011-06-24
forum: Hardware
---

### Post by steevven1 on 2011-06-24
I've installed Ubuntu 11.04 64-bit on my new ThinkPad X220, which, I believe, is "Ubuntu certified."

I have no major complaints except that my WiFi (which worked out of the box, no fiddling necessary) is EXTREMELY unstable, disconnecting me from the network I'm on every few minutes. When it is connected, the connection is very slow, even when I have a great signal, and on networks I have used with zero problems on other machines.

I'm 99% sure this is a hardware/driver issue, but I have no experience in solving such issues. Is there another driver I can try? How can I install it?

lspci gives me the following for wifi:
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)

THANK YOU!

---

### Post by steevven1 on 2011-06-24
I solved the problem by exactly following the instructions here:

[http://www.chayx.net/2011/06/how-to-install-realtek-rtl8188ce-wifi-drivers-thinkpad-edge-13-on-ubuntu-natty-1104.html](http://www.chayx.net/2011/06/how-to-install-realtek-rtl8188ce-wifi-drivers-thinkpad-edge-13-on-ubuntu-natty-1104.html)

---

