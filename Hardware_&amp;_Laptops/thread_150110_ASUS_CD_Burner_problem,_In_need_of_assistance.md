---
title: "ASUS CD Burner problem, In need of assistance"
date: 2006-03-25
forum: Hardware &amp; Laptops
---

### Post by kenatk on 2006-03-25
Hi and thank you for taking the time to read this. I recently installed Ubuntu Hoary Hedgehog an updated it, on a friends recommendation (I've been using Slackware Linux for about 3 years now). Anyway, I'm delighted with Ubuntu, but I do have a problem.

My CD burner doesn't work properly. The system recognizes it, but when I put a blank CD in there, it says there's no medium found in it.

Some specifics:

- my burner is an ASUS - CRW-5232AS

- in /dev/ I have entries for cdrom and cdrom1, cdrom corresponds to /dev/hdc and cdrom1 (my burner) corresponds to /dev/hdd

- I am using Kernel 2.6.10

K3b recognizes the burner just fine when I run it as root, or as my normal user. But when I select the burner in the upper left-hand corner of the K3b screen, it fails to recognize it, saying "No disk", even though there's blank CDRW in there. And of course, when I try to burn the disk it fails as well, telling me to insert a blank CD.

What can I do to resolve this problem? Any help is much appreciated, thank you very much.

---

### Post by StefanoCole on 2006-03-27
Hello, have you tried with different CD-R, CD-RW brands?
Also have you checked if a firmware upgrade for your burner is available from the manufacturer?

Stefano

---

