---
title: "hp pavilion dv6156 - feisty final - bcm43xx don't load in live cd mode"
date: 2007-04-19
forum: Hardware &amp; Laptops
---

### Post by zub on 2007-04-19
Hi all,
I am new here, and I pretty much enjoy ubuntu.

 I have downloaded the feisty last release today, and I am experiencing a problem with my laptop hp pavilion dv6156eu (or dv6153eu, I don't remember exactly). 

Once running in live-cd mode in order to test feisty (I have a the amd64 iso), the driver for my wlan card won't load; it seems that feisty tries to load the bcm43xx modules, but none of them works.

After a short stop, the cd keeps running, I see the brown screen, and I hear a repeted same short sequence of sound (bump-bump-bump-bump ad infinitum...), and nothing is happening. Is this possibly related to the wlan driver problem?

I tried to run with acpi=off and also with noapci and nolapic, but same problem; same problem also when I tried to run in safe graphic mode.
 
Thanks a lot for your help,

yours

zub

---

### Post by bloodniece on 2007-04-19
Sometimes WLAN cards are a bit dodgy in Live-CD mode.  Especially BCM (Broadcom-based) cards.

The only cards I've seen work from a Live CD (Ubuntu, Knoppix, or DSL) are Atheros and Ralink chipsets.

If you just want to peruse the Ubuntu desktop, just plug it into Ethernet and surf away. Later, if you decide to install, you can try one of the many Brroadcom WLAN driver solutions that exist.  Someone here can help you with that.

---

### Post by zub on 2007-04-20
Thank you for your post, I will try that right now.
yours
zub

---

### Post by zub on 2007-04-20
Hi,

I tried to normally boot with my wlan off and with a rj45 pluged in my machine. 

After feisty tries to load the hardware drivers, it displays a message saying that my laptop doesn't have enough buffering space ('... reveceiving uevent, not enough buffering space' or somthg like this). 

I reboot same with acpi=off; it reboots normally since I hit the brown screen, and remain stuck at it. Feisty doesn't bring me any further, it hangs there making the repetitive sound described above. 

I reboot without network and with acpi=off, but I get the same result.

Thanks again for your help

yours

zub

---

### Post by zub on 2007-04-20
Here some more details about my machine:

AMD rution 64 x2
1 Gig RAM
120 Gig HD
nvidia GeForce go 7200, 256 mb memory cache
integrated webcam 1,3 megapixels (Ricoh)
Broadcom WLAN (bcm43xx)
soudcard: SnD-HDA-NVIDIA

I always don't understand why I am not able to log in feisty. Any hints?
Thanks a lot in advance
yours
zub

---

### Post by zub on 2007-04-20
...really none helping little me?
[-o<

---

