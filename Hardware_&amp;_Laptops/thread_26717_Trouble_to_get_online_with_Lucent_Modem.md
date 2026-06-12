---
title: "Trouble to get online with Lucent Modem"
date: 2005-04-13
forum: Hardware &amp; Laptops
---

### Post by ludi on 2005-04-13
Hi.
I can't get online with my lucent/agere DSP winmodem.
The instalation is fine, everything in your place.
The big trouble is that when I connect (after the ppp negotiation) my system hang, not hang but brake. Just the mouse work, so I have to turn down by off button.
Then I've tried to use the pci=routeirq but when I use this option I can't load the lt_serial module (I get a "no device  or something like that" message in wvdial) and when I look up to my /dev I couldn't found the ttLTM0 (because of the lt_serial).
I've disable the plug&play OS on BIOS to be able to load the modules. When I try to load with this option on, I get a device busy or I/O error.
Please help. I need to work and this problem don't let me...

---

### Post by ludi on 2005-04-13
(I get a "no device or something like that" message in wvdial)
Sorry, in modprobe not in wvdial :)

---

### Post by ludi on 2005-04-13
[QUOTE=ludi]Hi.
I can't get online with my lucent/agere DSP winmodem.
The instalation is fine, everything in your place.
The big trouble is that when I connect (after the ppp negotiation) my system hang, not hang but brake. Just the mouse work, so I have to turn down by off button.
Then I've tried to use the pci=routeirq but when I use this option I can't load the lt_serial module (I get a "no device  or something like that" message in wvdial) and when I look up to my /dev I couldn't found the ttLTM0 (because of the lt_serial).
I've disable the plug&play OS on BIOS to be able to load the modules. When I try to load with this option on, I get a device busy or I/O error.
Please help. I need to work and this problem don't let me...[/QUOTE]
I'm using Ubuntu 5.04.

---

