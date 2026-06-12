---
title: "Asus P5B Ehternet Kernel Patch"
date: 2007-01-14
forum: Hardware &amp; Laptops
---

### Post by Wouterrrr on 2007-01-14
Hi,

I just can't seem to get my Ethernet working under ubuntu 6.10

Ive got a: Asus P5B Deluxe/WIFI motherboard

I tried to install the driver from the Asus cd, but the script needs to to patch the kernel, but the script needs also the linux source. :neutral: 

In /usr/src/ are only the headers of linux like linux-headers-2.6.17-10-generic, and not the source

I tried to get the linux source on:
CD: but it ins't there 
APT-Get: can't do that since ive got no internet
Kernel.org: Ive downloaded and unpacked linux-2.6.17-10, but this wont work (because its not the generic version I think)

Can anyone help?

Greetz,

Wouter

---

### Post by rocktorrentz on 2007-01-17
That's extremely odd. I've got a P5B and my ethernet worked out of the box; although I had to enable it in network manager.

---

### Post by cd1680 on 2007-01-17
how did you enable your network for your p5b? I tried going to system-->networking and I don't even see an option that says "wired connection". all I see is "Modem Connection".

---

### Post by Wouterrrr on 2007-01-19
It works now after Ive plugged the cable in the second ethernet connection :-# 

Ive read about this but I seemed to remember that only the first connection worked and not the second :neutral:

---

