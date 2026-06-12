---
title: "ATI Mobility 9700 on Acer Ferarri 3400 - Need help!"
date: 2007-01-11
forum: Hardware &amp; Laptops
---

### Post by xorfodan on 2007-01-11
Hi there,

I usually manage to fix things like this myself but this time it looks like I am going to need A LOT of help! I have been trying alot of distros lately and I just love Ubunutu Edgy 6.10 BUT after 1 week of trying to get my Radeon ATI Mobility 9700 to work I'm close to give up :( Can anyone help me please please please please. First of all is if anyone with a graphics card like me got it to work?!?! I have followed ALL HowTo's there is on this site.

Best regards

Chris

---

### Post by xorfodan on 2007-01-12
A *bump* for me

---

### Post by xorfodan on 2007-01-12
Never mind I got it to work the brutal way! I ripped out ALL the ATI / xorg packages in the Synaptic Package Manager and deleted the xorg.conf. REBOOTED without a xorg.conf file. Followed the tutorial found at [http://albertomilone.com/instructions.html](http://albertomilone.com/instructions.html) . In the tutorial it says that you have to add

Section "Extensions"
Option "Composite" "disabled"
EndSection

Do not add that, add this instead

Section "Extensions"
Option "Composite" "0"
EndSection

in xorg.conf.

Cheers

Chris

---

### Post by franestepona on 2007-01-13
If u disable composite u end up without beryl, isnt that true?? I want the drivers to work but dont want to lose beryl, I have direct rendering with no ATI propietary drivers though.

---

