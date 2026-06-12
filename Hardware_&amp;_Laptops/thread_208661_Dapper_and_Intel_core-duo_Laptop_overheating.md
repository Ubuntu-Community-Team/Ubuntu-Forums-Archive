---
title: "Dapper and Intel core-duo Laptop overheating"
date: 2006-07-03
forum: Hardware &amp; Laptops
---

### Post by Brachabre on 2006-07-03
I keep reading these posts around the web about ppl w/ dell's and intel coreduo's having problems w/ the ACPI and intel's speedstep frequency scaling not working correctly (also fans not turning on/off when they should)

This scares me a lot now. It's frightening me away from wanting to use linux on my laptop because of the fear of frying it.

---

### Post by dracolich on 2006-07-03
I just got done installing Dapper on my bran spanking new out of the box e1405. So far so good nothing has exploded yet and it dosent seem to be overheating at all.

---

### Post by Hellkeepa on 2006-07-04
HELLo!

These are only problems that seem to be related to the newest kernel, especially the -686 version. If you either install Breezy, use an older Kernel, or the -386 kernel you should have no really big issues with heat. As for the fans not working, these are very few issues, and only happens on a very few laptop configurations. So it's nothing to worry about really.

Happy codin'!

---

### Post by m94mni on 2006-07-04
You shouldn't really be afraid to try - you will notice in time if the laptop gets too hot.

My computer really has potential to overheat (given the oversize GPU), but it runs fine, fans work well, etc.

Running -386 instead of -686 will give you a non-SMP kernel, which is probably not what you want. Try the -686 kernel first, and switch if you see any problems.

---

### Post by insanedc on 2006-07-04
Do a search on ACPI, DSDT and Linux. Replacing the DSDT for your computer should address your overheating problems. I experienced erratic results with i8k because it and Linux were having problems reading the ACPI information form the BIOS in my Inspiron 8600.

---

