---
title: "Removing modem HW disables eth0"
date: 2006-12-05
forum: Hardware &amp; Laptops
---

### Post by n00buntu NJ on 2006-12-05
???

Ok, so right when I feel like I'm starting to know what I'm doing...

I've been tinkering with this computer for the past 9 months, and I haven't had a single problem... until now...

I discovered that one of my PCI slots is dead a while back, and I want to install my TV Tuner card again to give MythTV a shot in Edgy.

The only (working) PCI slot left is if I remove the dial-up modem card at the very bottom of the tower.
I did this and plugged in the TV Tuner card with no problems, only when I booted the computer back up I lost eth0 (no internet/network connection).  
After some googling on my laptop I decided to try to put the modem back in and see what would happen - sure enough, after I rebooted I had eth0 back!

This doesn't make any sense to me, and I don't have any idea of how to troubleshoot this...  

Any suggestions?

My goal is to remove the modem (cuz I'll never use it anyways), and use that last PCI slot for my TV Tuner card.

Any help is appreciated.

---

### Post by superm1 on 2006-12-05
Well first important question here, if you remove the modem, is the PCI device for the ethernet adapter still listed as a recognized PCI device?

You can check via ```
lspci
```

If it is no longer detected, then that is your bigger trouble here.  You mention a bad slot, but can you juggle cards around in other used slots and get similar results?

---

