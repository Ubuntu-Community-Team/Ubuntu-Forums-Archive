---
title: "DVD drive no longer detected by BIOS or Ubuntu"
date: 2008-03-13
forum: Hardware &amp; Laptops
---

### Post by Ebuntor on 2008-03-13
Hi,

Suddenly my laptop DVD drive is no longer detected by the BIOS or Ubuntu.
While watching a movie from the drive the system froze. After rebooting the system would lockup every time I inserted a disk. A few reboots later all my BIOS settings were reset and the DVD drive was no longer correctly listed. Previously it was something like "Samsung CD/DVD+-RW" now it's just "IDE: CD-ROM". It's called that in Ubuntu too now.

I tried manually mounting it but I get the error message "mount: special device /dev/hda does not exist". I can't even boot from a Live-CD. The drive does still seems to work though. When I insert a disk it does start spinning.

Could this be a hardware problem? I don't have a clue what I could be. 
I run Ubuntu 7.10 and my laptop is a Fujitsu Siemens Amilo PA 1510. 

Thanks in advance. :)

---

### Post by OffAxis on 2008-03-13
Usually when the BIOS drops it like that it's a hardware problem. 

There's two different firmwares you could try to Flash in the hopes of solving the problem. 
One is the motherboard's firmware (the BIOS). The fujitsu website should have it if there is one.

The other is the DVDROM's firmware. I don't know about your particular drive (especially on a laptop), but it might be worth a google search.

---

### Post by Ebuntor on 2008-03-13
> **OffAxis said:**
> Usually when the BIOS drops it like that it's a hardware problem. 

There's two different firmwares you could try to Flash in the hopes of solving the problem. 
One is the motherboard's firmware (the BIOS). The fujitsu website should have it if there is one.

The other is the DVDROM's firmware. I don't know about your particular drive (especially on a laptop), but it might be worth a google search.

Oh crap, I see. That's pretty bad. Do you know how something like that can happen so suddenly? 

As far as I can tell the Fujistu Siemens site only has Flash downloads for Windows and I don't have clue what exact model DVD drive I have so I guess I'm pretty screwed. :(

---

### Post by Ebuntor on 2008-03-13
Could I flash it via Wine or would that trash my hardware?

---

### Post by Ebuntor on 2008-03-15
bump

---

