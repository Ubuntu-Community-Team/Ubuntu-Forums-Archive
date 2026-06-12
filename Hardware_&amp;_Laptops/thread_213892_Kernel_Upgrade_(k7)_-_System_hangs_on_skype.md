---
title: "Kernel Upgrade (k7) - System hangs on skype"
date: 2006-07-11
forum: Hardware &amp; Laptops
---

### Post by afterxleep on 2006-07-11
Just installed Ubuntu on mu presario 2100 laptop (AMD), everything works out of the box.

Video is ok (ATI default driver installed).  Just changed to radeon and I have 3D acceleration.

Touchpad, wacom tablet, and inclusive an external wireless card (DWL 650) worked perfectly.

Just found Ubuntu installed the 386 kernel, so in order to optimize things, I installed the k7 kernel with amd support.   System behaves A LOT better.

The only things that really bothers me is that if I start skype, the whole 
system hangs as soon skype connects to the server and set me online.

This is not happening with the 386 kernel.

I think this could be related to the sound system, but no ideas. 

Does anyone have the same problem?

---

### Post by afterxleep on 2006-07-11
Okay, just started booting with all hardware devices unplugged and started to plug one by one after each reboot.

I found that the system freezes only when I am running kernel 2.6.15-25-k7 and start skype connected to the web using my DWL 650 PCMCIA wireless card.

If I'm on the wired network, everything works ok (even skype).

So it seems this issue is related with something skype does with the network that the wireless driver or kernel is not capable to understand.

Very weird.

---

### Post by kikiwitch on 2006-11-06
Ok Im running Edgy on an IBM X24 Laptop with docking station.

Skype has been locking up my system

 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux

Almost every time I have ran it.

I read what you said about your DWL wireless card, I have a DWL-610 PCMCIA card.

Just booted up cabled in to the lan with the wireless card unplugged and skype has loaded fine.

I will let you know if skype crashes again.

Thanks for your help!

---

