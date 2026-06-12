---
title: "Before I upgrade"
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by tropdoug on 2009-01-10
I need to find out one thing. Why does my /home folder show 12.4 gigs used with 41.8 gigs free making a total space of 54.2 gigs (obtained by right clicking the folder and going to properties) but when I examine my partition setup using gparted I find that the partition I set as my /home partition is showing 29.16 gigs used out of a total partition size of 74.72 gigs.

See attached screenshot's. 

is there a way to examine the directories and files using the terminal? What I am worried about is 

a) why is there this discrepancy
b) what causes it
c) Is my /home directory in fact on the partition it's supposed to be on, and if I do an upgrade to Ubuntu 8.10 will I still have all my files and configs etc or will I trash some required files?

Appreciate any help before going further.

---

### Post by Partyboi2 on 2009-01-10
> c) Is my /home directory in fact on the partition it's supposed to be on, and if I do an upgrade to Ubuntu 8.10 will I still have all my files and configs etc or will I trash some required files?
Your /home is on its own partition (sda3) Everything in your /home partition will be untouched when you do a upgrade. If you are doing a clean install of 8.10 then make sure to select "manual" at the partition stage and reset the mount point for sda3 to /home again.

---

### Post by tropdoug on 2009-01-10
that is what I thought, but then why is there this size discrepancy? if I am looking at the same directory but in different ways it should still show the same overall size. I know there are hidden files but surely those files would not equal another 11 something gigs?

---

