---
title: "Firewire used as network interface"
date: 2006-01-13
forum: Hardware &amp; Laptops
---

### Post by DeadEnd on 2006-01-13
Hi
When I install Ubuntu it does not detect my rt2500 wlan card,however it does detect a Firewire device then states it could be "used for a network interface".
I know for sure I have no firewire device, the only PCI card is my wlan so is it refering to that?
BTW if I skip network setup and manually configure wlan it all works,just curios as to why I get the message.

---

### Post by sudokubuntu on 2006-01-13
This would be interesting to know more about for me as well.
Wondering if I could connect through a Mac Powerbook G4 .
The Mac is on wlan.
If I could connect through it, it would have been very useful in times of wlan-problems   :???:

*edit* oops, maybe I got it wrong. But I have the exact same thing with my atheros card as well, so still interesting to me. And, of course, I could have used it during installation.

---

### Post by DeadEnd on 2006-01-14
Well for the sake of curiosity and it appers I am not unique.
Bump :)

---

### Post by DeadEnd on 2006-01-15
anyone?

---

### Post by nalmeth on 2006-01-15
I have a so-called firewire device aswell on my laptop (sony viao), and I don't have working wireless. As you might have read, I think this might be a 'firmware' issue, but if this is an option, hopefully solving this can solve both our problems.

Run lspci, and see if you have this same line:

0000:00:0e.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)

---

### Post by nalmeth on 2006-01-15
ahh sorry, this is not necessary for wireless devices. See here:
[http://en.wikipedia.org/wiki/Firewire](http://en.wikipedia.org/wiki/Firewire)
too bad. I thought I might have had something.

---

