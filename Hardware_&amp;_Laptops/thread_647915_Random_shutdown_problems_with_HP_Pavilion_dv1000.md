---
title: "Random shutdown problems with HP Pavilion dv1000"
date: 2007-12-22
forum: Hardware &amp; Laptops
---

### Post by treesnogger on 2007-12-22
Hi! I've been having random shutdown problems A LOT.

Usually, the computer will turn off and a black screen with information about what's failing will pop up. Sometimes the computer overheats, and if anyone has suggestions on how to offset that--it was a very rare problem when I ran windows, but gutsy and feisty have both had the issue--I would appreciate it, but I can usually prevent it by putting the computer on a noncloth surface.

The shutdowns that are really driving me crazy usually have information about some USB port problem (the next time it happens, I'll try to write down exactly what, but usually it scrolls by too quickly) or say something about the message bus daemon failing.

Has anyone had a simliar problem? Any suggestions??

Thank you so much!!

---

### Post by PeteyChristiansen on 2008-02-18
I have a dv1000 running dual-boot xp home and Ubuntu 7.04 (feisty?).  I have not once had the problem you are describing of the usb error, nor have I had fan problems.  If anything, I noticed that the fan tends to run more often in Ubuntu than windows.  Concerning the USB, do you have any USB devices actively connected to the system?  

Oh, and have you gotten your wireless working?  Just curious, since that's the only issue I've really had.

---

### Post by Yellow Pasque on 2008-02-19
Try looking at Applications -> System Tools -> System Logs or:
```
dmesg | grep USB
dmesg | bus
```
etc...

---

