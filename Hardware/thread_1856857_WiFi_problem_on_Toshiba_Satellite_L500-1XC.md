---
title: "WiFi problem on Toshiba Satellite L500-1XC"
date: 2011-10-09
forum: Hardware
---

### Post by ottaky on 2011-10-09
Hi guys,

my wife has a Toshiba Satellite L500-1XC. I installed 10.04 on the machine when we bought it last year and it's worked fine ever since.

On Friday I ditched my Sky ADSL package (which we never had any problems using) and moved over to BT's Infinity, but I'm having problems with the WiFi.

The laptop can see the router. I can connect to the router. I can ping all of the other wireless devices (2 x Android phones, 1 x Android tablet). I can ssh to my desktop PC (which is wired via ethernet into the hub). Basically, everything looks good.

However, as soon as I try to access a host on the internet (anything outside of my local network) the connection suffers crippling packet loss (anything between 30 - 100% loss). Webpages take forever to load, if they load at all. Pinging [www.google.com](www.google.com) sometimes works, sometimes not - when it works the majority of the packets are dropped.

Looks like I'm using the r8192se_pci kernel module (Realtek), and nothing obviously bad shows up in /var/log/messages.

Everything looks right .. but I can't figure out what's causing the problems. When I boot the laptop into windows, everything is fine - so I'm assuming it's something Ubuntu related.

Anybody have any ides??

Many thanks!

sjb

---

