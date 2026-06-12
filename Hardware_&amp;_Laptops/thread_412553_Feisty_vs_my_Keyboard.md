---
title: "Feisty vs my Keyboard"
date: 2007-04-18
forum: Hardware &amp; Laptops
---

### Post by masked_marsoe on 2007-04-18
Feisty and my keyboard don't like each other. I'm not getting proper responses from it, letters go missing as I type, and there is significant lag. 

There hasn't been a problem since I installed 5.10 and worked my way along the versions. 

I'm running Xubuntu Feisty beta, on a NEC Versa A2100 laptop, with what it calls a "Microsoft Standard" keyboard. 

In addition, the mouse pad lags or is jerky. 
A usb mouse works fine, so the problem is definitely with the on-board gear.

I'd rather fix it than roll back, because of the prospect of losing Ubuntu in the future.

---

### Post by old_geekster on 2007-04-18
I am certain that someone will have the same problem once the final version is released.  So, be patient.  You will have help soon --- hopefully.

One thing, did you go to "Keyboard" (System/Preferences/Keyboard/Layouts) and experiment with different Keyboard models?  I have solved a problem by this means.

Good luck!

p.s. My keyboard is the only component that is not functioning 100%.  I have a Logitech Mx700 Duo (Wireless Kbd/Mouse).  Many of the special keys don't work.  I will attempt to solve the problem later.

---

### Post by lost_sole on 2007-04-20
These are exactly the symptoms I was experiencing. I had 6.10 installed without issue but then did a fresh install of 7.04 yesterday and found my usb mouse and keyboard lagged terribly so much so that I would loose keystrokes or they would repeat. If the keyboard was not plugged in on boot, it would not even work at all.

 I did not have a ps2 option, but viewing through a remote vnc client worked perfectly. I assumed it was a usb issue and found this thread talking about irqpoll. Adding irqpoll as a boot option to the default kernel line in /boot/grub/menu.lst solved my problem. There is no more lag after a reboot.

[http://ubuntuforums.org/showthread.php?t=196413](http://ubuntuforums.org/showthread.php?t=196413)

---

### Post by masked_marsoe on 2007-04-21
Unfortunately, this is still a problem, taking off X configuration seems to have helped a little, but it's still not perfect like before.

---

