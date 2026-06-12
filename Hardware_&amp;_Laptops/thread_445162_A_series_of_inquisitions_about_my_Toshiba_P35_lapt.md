---
title: "A series of inquisitions about my Toshiba P35 laptop"
date: 2007-05-15
forum: Hardware &amp; Laptops
---

### Post by Death_Sargent on 2007-05-15
first off is home come tosh utils and tosh set both respond as lacking kernel support or just not working.

two how can i get my built in 7 in 2 card reader to work. 

finally do i have to do anything to make my PCI slot work because the last card i tried did not actually work.

Allso i note that periodically gkrellm reports data being moved on my ath0 wifi card. 

the data is heading inwards and i have no way of ascertaining what it is. it only happens when connected to the net and it may be related to the fact that when i have one of the bellow listed combinations running gnome freezes and is completely un responsive

```
firefox and a gnome terminal with irc being shutdown

gnome terminal and irc

xfce terminal and irc

xfce terminal and firefox with irc.

fire fox and an irc

just irc

a terminal and synaptic
```

i have tested with both kopete and gaim and the results are the same for both

---

### Post by lvflashguru on 2007-10-21
Greetings,

Shortly after installing Ubuntu 7.04 on my P35, I experienced problems very similair to yours.  Ran great for a little while, but as soon as I tried plugging in a usb webcam and opening up any webcam capture app, the whole system would freeze up and the only way to get it back was to hard reboot it.  I have a broken usb port and I can see in my dmesg there are repeated entries where the machine thinks something is plugged in, but cannot identify it.  Yet it tries over and over to assign an address to it.  I just figured there was some sort of conflict with this mystery device and my webcam.  Shortly after that, the problem got worse and the machine was totally unuseable, even without the camera or anything plugged in.  The touchpad would get more and more sluggish until the whole machine locked up again and again. 

Hours and hours of struggle finally brought me to my solution.  I noticed when the computer booted up for just a split second it showed a message referring to a bug and it had a bug number and some sryptic message about "no timer blah blah apic somethingerother".  I guess it's a pretty common problem with apic(I am totally pretending to know what that is) but the solution I found was to add "noapic" to the boot options in grub.  Ever since then the problem is gone and the machine runs like a dream!  

Good luck, hope this helped.

---

