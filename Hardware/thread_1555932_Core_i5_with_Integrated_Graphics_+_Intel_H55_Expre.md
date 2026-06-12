---
title: "Core i5 with Integrated Graphics + Intel H55 Express Chipset"
date: 2010-08-18
forum: Hardware
---

### Post by icmp.request on 2010-08-18
Hello! I'm thinking of buying a **corei5-660** on a motherboard with an **Intel H55 Express Chipset**. 
 
Does anyone know if it's fully compatible with **Ubuntu 10.04 TLS** ?
 
I mean video (that comes from the processor, not off-board PCI), audio (HD Audio), networking (Intel® 82578DC Gigabit), SATA Controller, USB, etc. 
 
I've tried to google but didn't find much info so I wonder if anyone is using or knows where I can find more info about it... 

I've found on Wiki info about a very similar motherboard ( [https://wiki.ubuntu.com/Intel_DH55TC](https://wiki.ubuntu.com/Intel_DH55TC) ) but I don't know if the person who wrote was using the processor graphics or off-board graphics...
 
Thanks in advance!

---

### Post by icmp.request on 2010-08-21
What about **Intel P55 Express Chipset **with off-board video have anyone tried?

---

### Post by maros.ivanco on 2010-11-20
I have just tried. Even though with i5 661. Spent the whole night. 10.10 64 repeatedly hangs during installation. 10.04 LTS installs, but the display is blurry and shaky - almost unreadable. With my deepest regret, after many, many years of attempting to use it, I finally proclaim linux to be the piece of... crap.

---

### Post by icmp.request on 2010-11-20
> **maros.ivanco said:**
> I have just tried. Even though with i5 661. Spent the whole night. 10.10 64 repeatedly hangs during installation. 10.04 LTS installs, but the display is blurry and shaky - almost unreadable. With my deepest regret, after many, many years of attempting to use it, I finally proclaim linux to be the piece of... crap.

Maybe you should try other distros first... Not everyone needs to like the most popular ones.

I'm glad to report that Core i5 760 with P55 Express Chipset works just fine...

But it has not integrated graphics. The graphic card is off-board.

---

### Post by alanmoore78 on 2010-11-20
Thank you for this post, I will remove the H55 from my build ideas for now.  I plan to use a video card anyway, but P55 will be the chipset I'll use if I go LGA1156.  Microcenter has good prices on LGA1156 chips, $40 and more off the MSRP so they're in line with equals from AMD.  But for now, the $199 Phenom II X6 1075T is what I'd LIKE to use.

---

### Post by Rusga on 2010-11-21
My PC is using the H55 chipset with an I3 550 and runs 64bit Unbuntu 10.10 fine (did hang a couple of times during installation though). The motherboard supports vga, dvi and hdmi output, I'm not sure if dvi or hdmi work as I'm only using vga.

---

### Post by magneze on 2010-12-17
Yep, I just booted 10.10 64-bit on an i5 660 + H55 with integrated graphics. The display is _very_ shaky. Windows 7 boots fine so the hardware is all ok (which I was worried about as I just built it).

So, I'd really like to use Ubuntu - anyone gone the i5 + H55 integrated graphics working?

---

### Post by ofir_k on 2010-12-22
I have this problem too with core i5 and intel mhd 4500.

I opened a bug report in LP:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/692673](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/692673)

Please comment there too so the devs will know that more have this problem.

---

### Post by deanjm1963 on 2010-12-22
Clarkdale (i5XX) graphics don't play nice with 10.04 - you need to use 10.10 which contains the latest version of the intel driver.

---

### Post by ofir_k on 2010-12-22
I am using version 10.10 (of kubuntu).

Do you know how can I investigate it further?

---

