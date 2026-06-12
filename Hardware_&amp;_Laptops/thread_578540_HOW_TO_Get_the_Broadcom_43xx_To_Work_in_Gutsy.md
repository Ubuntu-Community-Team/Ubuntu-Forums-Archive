---
title: "HOW TO: Get the Broadcom 43xx To Work in Gutsy"
date: 2007-10-17
forum: Hardware &amp; Laptops
---

### Post by bsalt on 2007-10-17
In Gutsy, this card is semi-supported. But one major problem is the firmware does not autoload on startup.

Here is my suggestion to get it working. For now at least.




I'm guessing you also have an ethernet device, so plug yourself into the internet somewhere. Open up Restricted Drivers Manager located in System -> Administration.


Enable the bit talking about firmware for a Broadcom something or other.



On my friend's laptop, she had the Dell 1300 PCMCIA wireless card, and when I enabled the firmware, the lights lit up. I was happy. On reboot, however, it does not autoload the module for it. So here's what I did as a fix until I know a better way to do so.



Go to System -> Preferences -> Sessions and create a new startup entry.


Type this in for the command:
```
gksudo modprobe bcm43xx
```



Now when you login, you'll have to enter your password again, but your card will be activated until I or someone else has a better idea.

---

### Post by JulienPDX on 2007-10-19
okay, so i discovered that enabling the driver actually worked somewhat "out of the box" for me on a Compaq Presario V6107US.  However, I have noticed that my college wireless (completely public network) frequently cuts in and out and i lose my connection.  How does one combat that? I am frequently having to "reconnect" to the wireless network b/c after a period of inactivity i get no activity; even though my connection claims to still be connected.


Like just now, after typing this, I had to reload the connection because I lost data transfer.  Very frustrating.

---

