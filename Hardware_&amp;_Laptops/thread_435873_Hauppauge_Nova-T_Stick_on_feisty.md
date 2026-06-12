---
title: "Hauppauge Nova-T Stick on feisty"
date: 2007-05-07
forum: Hardware &amp; Laptops
---

### Post by neocookie on 2007-05-07
Hi all

I'm having a little trouble with my Nova-T USB2 Stick under feisty. Things were working fine in efty.

I've installed the correct firmware (based on much googling), and now i can see the correct initialization messages in /var/log/messages. force_lna_activiation is set to 1, which I've confirmed. However, a 'scan' produces the following:

# scan -c -5 > ~/.xine/channels.conf 
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
dumping lists (0 services)
Done.

I've tried both the small aerial that it comes with and the main roof-top aerial, but neither work. I've also checked using the dvb-t file for my local mast, with no luck.

Is there anything else I can try?

---

### Post by dentaku65 on 2007-05-11
Did you tried with Kaffeine? I have the same TV USB and works pretty well with kaffeine... sometimes I have some trouble with the usb2 module of the kernel (can't tuve dvb) but unplug and plug the card reset the situation...

---

### Post by neocookie on 2007-05-12
yep, tried kaffeine. won't scan properly at all, and thats using both the supplied and main aerials.

Seems since my upgrade I'm having no luck whatsoever with feisty, and rolling back to edgy won't get me back to the same state.

---

### Post by flowerdealer on 2007-05-23
I have a similar problem. I install the driver, and it detects the nova-t stick. I can get it to scan using Kaffeine, and even get reception sometimes, but after a while there is a problem, the image is lost and I get an error message in the log. After that the only option is to restart the machine, although at restart the tuner almost never works.

---

