---
title: "Netbook touchpad problems (DNS netbook p10b series)"
date: 2012-04-27
forum: Hardware
---

### Post by Zeddushka on 2012-04-27
Hi ubuntuforums!
I'm sorry for my english.

I'm using netbook [http://krasnodar.dns-shop.ru/catalog/i128811/101-noutbuk-dns.html](http://krasnodar.dns-shop.ru/catalog/i128811/101-noutbuk-dns.html)
(i't russian site, but i write you all important information):

The problem is Synaptics Touchpad. On some linux debian-based systems/linux kernels this touchpad doesnt found by system (nothing in "xinput -list"). But in ubuntu 10.04 and 12.04 (and in debian squeeze) this touchpad represents as "PS/2 Optical Mouse" but still doesnt work. Adding file /etc/modprobe.d/options.conf wich contains: "options psmouse proto=imps" make them works!
[sory for this long prelude, but i still think that this can help solve problem...]
But in ubuntu 12.04 it works untill my netbook will be bootet without plugged power source. if i unplug power source when it works - touchpad works. but if i boot system whhithout plugged ac adapter - system lost touchpad forever! (rebooting with plugged power source doesnt help, reinstalling system make him visible again as "PS/2 Optical Mouse").
In debian squeeze it works properly, but i wery interested in ubuntu on my netbook...

Than you for your time, I hope you can help me solve this problem.

---

### Post by Zeddushka on 2012-04-27
SOLVED: installed kernel from lucid (touchpad work after suspend-wake action, when added /etc/modprobe.d/options.conf).

---

