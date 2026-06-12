---
title: "Keys/Touchpad not working on Lenovo y500"
date: 2007-10-15
forum: Hardware &amp; Laptops
---

### Post by venkatachar on 2007-10-15
Hi,
  I have Lenovo y500 and I was trying Ubuntu 7.10 rc .
I booted it up using the live CD after booting up none of the Keys worked and even my Touchpad was not working. However I connected external USB Mouse and it worked.

Is any one facing the same problem? 

Will this problem get resolved if I install the OS.
(I am planing to install 7.10 not Release Candidate)

---

### Post by gregraubie on 2007-11-15
I have the same problem when using Ubuntu 7.04 (live).

I tried a live CD of Kubuntu 7.10 and the keyboard and touchpad worked.
What is different between the two?

---

### Post by aashay on 2007-11-27
same here
[http://ubuntuforums.org/showthread.php?t=622698](http://ubuntuforums.org/showthread.php?t=622698)
No replies
Did it work with the final gutsy?

---

### Post by rmsrohan on 2007-12-23
had the same prob but after lots of googlin found that adding 

locale=fr_FR i8042.reset to your kernel line solves the problem with no error on sound or others


eg: 

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.22-14-generic ro quiet splash **locale=fr_FR i8042.reset**
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

---

### Post by vnkatesh on 2008-01-17
thank you.

was of great help.

---

### Post by vishalvishnoi on 2008-07-22
its working for me! thank you!

---

