---
title: "ide controller"
date: 2007-12-13
forum: Hardware &amp; Laptops
---

### Post by SyCo123 on 2007-12-13
Hi I have and old HP 8756C with a 40GB IDE HDD and a 500GB SATA drive connected to a rosewill rc-212 PCI  IDE controller.

I've just installed 7.10 server edition and then the xfce desktop. The IDE controller is throwing an error on boot

"expansion ROM not initalized - PCI mass storage Controller in slot 2" 
Bus:01 Device:09, Function:00
Press <F1> to set up, <F2> to resume

This PC is supposed to be a file server. Can I use Ubuntu or am I forced to go back and set this up as a WAMP server instead? I would really like to get this working in Ubuntu.

Is it possible to use an RC-212 or am I screwed?

---

### Post by SyCo123 on 2007-12-16
Still hoping for a little legendary community support on this issue. :)

I've removed the PCI modem and wireless card to reduce the demand for ROM (as suggested on Linuxquestions) . Moved the controller into slot one, to rule out a bad PCI slot, but the message remains. (only now refers to slot 1)

I've updated the BIOS too, to the latest version I could find
[http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?dlc=en&lc=en&os=209&product=58195&lang=en&cc=us&softwareitem=pv-17893-1](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?dlc=en&lc=en&os=209&product=58195&lang=en&cc=us&softwareitem=pv-17893-1)

Still no joy,

This happens before the OS is loaded but even so I  tried reinstalling XP but still no good.

See the lengths I've gone too. XP, man I thought I was done with that * $#!t.* 

Simon
A desperate man.

---

