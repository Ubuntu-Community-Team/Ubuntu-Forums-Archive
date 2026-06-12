---
title: "Touchpad problem: cursor jumps (Ubuntu 12.10, 64bits)"
date: 2012-12-26
forum: Hardware
---

### Post by Eolith on 2012-12-26
Hello, 

I have this annoying touchpad problem:  I move the  pointer with the touchpad. Then, at the end of the movement (i.e. when I  release contact with the trackpad) the pointer makes a small jump on  the screen of random magnitude and direction. 

This makes the laptop very hard to use since I have to aim 2 or 3 times before it lands on the right place where I want to click. As a result I very often click on the wrong place!

I have a new HP Pavilion  dv7 triple-boot with Ubuntu 12.10 (64bit), Windows 7, Linux Mint 13 (MATE, 64bit). It has a SynPS/2 Synaptics Touchpad.  

Booting with Windows 7 *does* *not* show this issue, indicating to me that  the touchpad H/W is ok. 

Mint 13 *does* show the same problem, as wel as Fedora booted from a live USB, leading me to conclude that this is a Linux-distro (driver?) problem. 

Incidentally, using a separate mouse works completely  fine.

I have searched in Linux forums, in particular this one, but I cannot find a solution. Any help would be welcome! 

Best regards, Eolith

---

### Post by DorianX on 2012-12-26
Does this happen right away, or only after you've been using the machine for some time?

I've got a stand-alone USB touchpad and I've noticed similar behavior but it doesn't kick in until the machine has been running more than a day. In my case, unplugging and replugging the touchpad makes the problem go away for a short time. Obviously you can't do that, but your touchpad is probably also connected to the USB bus "under the hood" so maybe there's a way to simulate unplugging and re-plugging.  My device is a Cirque Corporation 9925 AG, in case that helps anyone reading narrow down the scope of the problem.

---

### Post by Eolith on 2012-12-26
No. Problem occurs right away when I start machine and it persists no matter how long it's on. 

Under Windows 7 all works just fine so somehow "under the hood" unplugging and re-plugging I think is unlikely to help. Still: thanks for the suggestion and keen to try if anyone knew how to do that!

---

### Post by Eolith on 2012-12-29
Please - is there *anybody* who can help or provide any hints, or suggest on where else to look? Your help would be greatly appreciated!

---

### Post by DorianX on 2012-12-31
I can add that I tried using xinput to disable and re-enable the touchpad, and that didn't fix the problem. I'm trying to work out if there's a software way to reset the USB port since unplugging and replugging all the time probably isn't good for the connector.

---

### Post by elj4176 on 2013-01-12
I have the same problem on 2 new HP laptops. The touchpad is too sensitive. The touchpad settings sliders in the control panel do not seem to matter either.

I have to use an external mouse or it is nearly unusable.

---

