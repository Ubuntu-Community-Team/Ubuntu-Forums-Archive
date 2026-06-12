---
title: "Inspiron wireless light now working!"
date: 2009-03-11
forum: Hardware
---

### Post by Alexis Phoenix on 2009-03-11
Okay I know this may seem like a silly thing, but it makes me very happy and I wanted to share it!
I originally had Feisty installed on this Dell Inspiron 1501 laptop, and the wireless button turned the card on and off, and the light went on and off with it.
Since then, I upgraded first to Gutsy then Hardy, and all through this, and a number of home brew kernels, the button turned the card on and off, but not the light that tells you it's working.  However, since I went through my kernel config very carefully (now on 2.6.28 ) it works correctly again, and I am a happy bunny.  Strangely enough, I disabled most of the LED stuff this time...

(Now I just want to make the one work that toggles the external vga socket...)

If anyone wants my kernel config, please shout and I'll post it here.

Cheers
Alexis Phoenix

---

### Post by Ichido on 2009-05-07
When I first received my Dell inspiron 1525n, the LEDs had problems.
From the Dell Support Forum, I got a 'fix' for it.

Description: WiFi LED on system does not work. 
Systems Affected: Inspiron E1505n, 1420n, 1525n and XPS M1330n. 
Impact: WiFi LED on system does not turn on when WiFi is in use, but wireless still works. 
Fix: Install linux-backports-modules for your kernel. For example, if running kernel 2.6.24-16-generic: 
$ sudo apt-get install linux-backports-modules-2.6.24-16-generic

---

### Post by Kareeser on 2009-05-07
Fix didn't work for me, unfortunately. For whatever reason, installing the backports modules for my kernel totally futzed around with my wireless card, so it wouldn't even connect to a wireless network.

As of Jaunty, the LED is perma-on... heh heh.

---

