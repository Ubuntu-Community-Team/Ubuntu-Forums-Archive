---
title: "Getting past GRUB ..."
date: 2009-01-05
forum: Installation &amp; Upgrades
---

### Post by stoopid_noob on 2009-01-05
Hello,

The other night I made a stupid mistake. In short I had two USB keys, one with SUPER GRUB on it and the other with Windows XP. I accidentally formatted the key that SUPER GRUB disk was on after I just removed the Ubuntu partition using it. 

I am now stuck to where Grub 1.5 does not see an OS, which is correct, and there is no way to get around it. Nor do I have a USB key version of SUPER GRUB. 

Take note that this is on a Acer Aspire One machine with no CD or floppy. 

I would like to remove grub completely and put WindowsXPSP3 back on, I need my software compatibility back! 

What are my options? Please help. :confused::confused:

---

### Post by caljohnsmith on 2009-01-05
How about booting your Windows USB stick, go to the recovery console and run:
```
fixmbr
```
That should enable you to boot directly into Windows. Let me know how that goes or if you run into problems.

---

