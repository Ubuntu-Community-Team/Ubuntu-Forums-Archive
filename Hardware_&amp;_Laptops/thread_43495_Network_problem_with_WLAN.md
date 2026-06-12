---
title: "Network problem with WLAN"
date: 2005-06-22
forum: Hardware &amp; Laptops
---

### Post by robux on 2005-06-22
Hi, I have installed Ubuntu linux on an HP Laptop with an PCMCIA WLAN Card "ZyAIR B-120 from ZyXEL". 

After booting, the lights of my WLAN card are on, but they aren't blinking. So I think, that the card wasn't recognized well.

Can I install any DEB file or do I have to build my own kernel?

Do I have to download additional DEB files for general WLAN support?

Thank you!!!

---

### Post by sam1967 on 2005-06-22
first thing to do is 

cardctl ident 

iwconfig

iwpriv

ifconfig

post results here

---

### Post by robux on 2005-06-23
[QUOTE=sam1967]first thing to do is 

cardctl ident 

iwconfig

iwpriv

ifconfig

post results here[/QUOTE]

Ok, here are my results:

cardctl ident:
product info: "ZyAIR", "B120 802.11 Wireles LAN", "Version 1.00",""
manfid: 0x0308, 0x3401
function: 6 (network)

iwconfig:
eth0 no wireless extensions

iwpriv:
eth0 no private ioctls

ifconfig:
empty

---

### Post by gotaserena on 2006-01-02
Sorry to bring back this thread, but I'm running through the same problem, and tried everything to solve it. If you google around enough for hints on how make this card work you'll find a link to zyxel danish site where you can download the linux-wlan-ng package **for 2.4.x kernels**. I've installed the newest stable version of linux-wlan-ng but I still am not able to make the card work with  the prism2_cs module it's supposed to.

Any help would be greatly appreciated.

---

### Post by mattisf on 2006-01-02
Hey,

I have a Zyxel PCI-card. I had to use the "ndiswrapper" to make it work. (Search the forums for ndiswrapper and wireless and I'm sure you'll find something useful.) This is a tool that allows you to use windows drivers on Linux. 

Also, are you sure there's a prism chip in there? Mine is not... Although mine is not the pcmcia model, either, so it could very well be different.

Cheers,

Mattis

(Edit: typo.)

---

### Post by gotaserena on 2006-01-04
Hei mattisf,

thanks for the answer. I was poking around wlan-ng page and found that the b-120 has a zydas chip, not a prism one. So I guess you're right. Funny thing is that this card works out of the box in my KISS DVD drive which runs on some sort of embedded linux based on the 2.4.x kernel. That's why I was hoping to get it to work natively on my laptops.

---

