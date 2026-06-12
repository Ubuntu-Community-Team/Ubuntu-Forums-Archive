---
title: "No keyboard  and trackpad ACER 5553g laptop"
date: 2010-08-17
forum: Hardware
---

### Post by GregTaylor on 2010-08-17
I recently purchased an ACER aspire 5553g laptop.

I installed Ubuntu 10.04 on it and had a few setup problems that I'm trying to solve.

The first problem I tried to solve was that it wouldn't detect the battery. To solve this I performed a bios update and it worked, now I can detect the battery and monitor it.

HOWEVER, I have lost the use of the keyboard and trackpad (quite a bit more annoying)

I have tried to boot using a live CD (ubuntu & openSUSE) and still no keyboard or trackpad.


Can someone help me ??? 

Greg

---

### Post by Fafler on 2010-08-17
Try tinkering around in the BIOS setup. There might be an option for USB legacy support or something.

---

### Post by GregTaylor on 2010-08-17
Alas, there's not much to tinker with in this bios (no usb options). I tried all the settings but no luck.

---

### Post by amaranthius on 2010-08-20
I'm facing the exact same problem. After flashing the BIOS  i got the "Disabling IRQ18" message during startup and the keyboard was gone. After some googling and digging in forums I tried passing various options to grub like 'noirqdebug' and 'irqpoll' but with no luck. I also tried running the latest Arch live cd, but with the same result.

If anybody finds a solution/workaround, please share it.

---

### Post by amaranthius on 2010-08-21
After many hours of banging my head against a concrete wall I've found a workaround. It's far from the best, but at least I can use my system again: 

passed ```
acpi=off
``` to grub and it worked but **fglrx** complained ```
ACPI is disabled on this system
``` and failed to load KDE. To get around this I did ```
modeprobe radeon
``` and edited the line ```
Driver  "fglrx"
``` in /etc/X11/xorg.conf to ```
Driver  "radeon"
```**startx **then worked like a charm. I still haven't tried making this the default startup behavior, but it shouldn't be hard. 

Hope this helps!

P.S. I still think a bug should be reported because this problem is quite annoying.

P.P.S. Oh, and of course, forget about battery detection ;)

---

### Post by amaranthius on 2010-08-26
SOLVED: Updating the BIOS to  v1.17 fixed the keyboard problem.

---

### Post by GregTaylor on 2010-08-27
Wow,

A big thank you for the workaround.

I'll try the bios update. I'm glad they got around to a new bios, when I contacted acer they wanted me to send in the laptop.

I've been running ubuntu in virtual box since then.

---

### Post by GregTaylor on 2010-08-27
The bios update works for me too!

Now on to minor problems.

Solved:p

---

### Post by amaranthius on 2010-08-28
Hey, no problem! Glad to hear everything's OK. 
Heh, when I contacted acer i didn't receive any response at all :D One day I just decided to check if, by any chance, there's a new BIOS and what do you know! :)

---

### Post by daanemanz on 2010-09-11
Wow... thanks!

I've been struggling with this since I bought my laptop 3 months ago. I thought I'd be stuck with Windows 7 forever :rolleyes:

---

### Post by Hypercore on 2010-09-18
Hey, could someone please supply me with a link to the v1.17 BIOS update? I'm having the same problem yet I can't seem to find a download for 1.17.
 
Any help would be appreciated.

---

### Post by daanemanz on 2010-10-07
Well, here you go...

[http://bit.ly/1ZcReU](http://bit.ly/1ZcReU)

Or just look around on the Acer website. You can find this in the Service & Support section.

Good luck!

---

