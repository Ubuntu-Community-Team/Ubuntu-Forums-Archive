---
title: "Ubuntu on a Asus A6 Notebook?"
date: 2006-07-26
forum: Hardware &amp; Laptops
---

### Post by hans.spoed on 2006-07-26
Hello,

Is someone running Ubuntu on a Asus A6-series notebook? I am, and I'm quite enthousiastic except for the wireless connection which just won't work. :x 

I have the idea the wireless card is switched off despite the burning led. I just can't get it to work.

Any experienced asus users in here?

---

### Post by Paerez on 2006-07-26
I am not an experienced asus user, but I'll help you troubleshoot your card...

---

### Post by krazyd on 2006-07-26
Yep, I've had Ubuntu running on an A6KT.

Two problems which I had which made the OS pretty much unuseable:
1. Freeze on boot if anything is plugged into USB. (apparently an issue with ACPI / BIOS, hopefully updated kernel in edgy will fix this)
2. Dodgy ATI drivers.

The wireless card (Broadcom chip, mine's a 4318 rev02) works fine, however. If you install ndiswrapper and network-manager, you can even use WPA! :D I'd recommend ndiswrapper over the native bcm43xx at the moment because the native driver still has some issues especially with this particular chip.

Which particular A6 model do you have?

---

### Post by admlv on 2006-07-27
Hi!
I'm using Dapper on Asus a6u laptop. Wirles is working fine witht Broadcom chip using native driver. If you hav Broadcom wirless chip too then i sugest you to look in wiki for documentation kow to get it work with native driver. The main problem is that Ubuntu dont have included firmware package witch is needed to Broadcom based card to work. At the begining I tried to use ndiswraper folowing how-to but without results. With native driver - about a half of hour and it's working.

---

### Post by [h2o] on 2006-07-27
I got DApper runing on a A6k and besides the webcam not working (and mine is seem to not be a m560x, but a syntek semicon and thus the current driver project won't be able to help me :() everything is more or less working as expected. I have not tried everything since installing Dapper yesterday (I ran Dapper Beta in may/april but did a swith to Suse, but returned since installing packages on Suse was a pain in the ***) but so far so good.

---

### Post by pcolamar on 2006-08-04
Almost same situation here.

Dapper on A6kt (AMD Turion ) with Xgl+Compiz (shocking !)

WiFi via internal driver (Wep)

Same problem with the webcam and I have not succeded to set the lm-sensors so far

---

