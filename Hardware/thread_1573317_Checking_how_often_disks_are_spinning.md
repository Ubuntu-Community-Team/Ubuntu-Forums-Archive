---
title: "Checking how often disks are spinning"
date: 2010-09-12
forum: Hardware
---

### Post by anjames on 2010-09-12
Hey folks,

Looking through the forums I find lots of people around playing with the settings of their disks to try optimizing how often they should be spun down, but as much as I've tried I haven't found any way of checking specifically how often a disk is spun up. I checked the man page for hdparm, but I can't find anything about querying the spin status of a disk. 

I was hoping to log any disk spin status changes so that I could go through the history of a system and figure out how long disks were spun up to debug if they're getting brought out of standby unnecessarily, but I can't even figure out how to probe the status in the first place!

Any ideas?

---

### Post by anjames on 2010-09-12
As usual, more digging around unearthed a decent answer: 'smartctl -a' lists all sorts of info about disk run time.:D

---

