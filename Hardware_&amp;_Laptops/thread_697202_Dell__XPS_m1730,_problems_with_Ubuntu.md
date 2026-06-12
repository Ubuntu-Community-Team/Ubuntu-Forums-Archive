---
title: "Dell  XPS m1730, problems with Ubuntu"
date: 2008-02-14
forum: Hardware &amp; Laptops
---

### Post by XziviT on 2008-02-14
Well ive been trying to install the damn ubuntu from the 7.04 and 7.10 wubi versions, i also found a link to the 8.04 and non of these work, with the 7.10 i had the oportunity to log into ubuntu but when i logged off and tried to go in with the startx command the image to log in looks warped and i cant see anything i write, and when i log in a message appears and i cant read it then i press escape to go back to the black screen with letters and it says something about the x server, i had a problem with the x server with every version i installed and i dont know what to do, please help me, ive been asking alot of stuff about the x server and no1 can give me an accurate answer please tell me what do i NEED to download or do to end with this problem.

And someone told me that the alpha 4 i dont even know what the hell alpha 4 or 3 or 100 means but someone told me that that thing has problems with the newest video cards and that the new alpha 5 will support them.
A problem with an old card is impossible because my XPS is only a month old and it has one of the best and newest cards in the market. So as i said please help me with REAL ANSWERS.:confused:

Thanks.

---

### Post by Murphy2712 on 2008-02-15
Hey, please make shorter sentences !
It's because your hardware is new that it's not working fine.
Try adding "noapic" parameter to your kernel option (for me I press c to edit the grub menu).
And look at your logs (cat /var/log/X..) and (dmesg).

---

### Post by macabro22 on 2008-02-16
> **XziviT said:**
> Well ive been trying to install the damn ubuntu from the 7.04 and 7.10 wubi versions, i also found a link to the 8.04 and non of these work, with the 7.10 i had the oportunity to log into ubuntu but when i logged off and tried to go in with the startx command the image to log in looks warped and i cant see anything i write, and when i log in a message appears and i cant read it then i press escape to go back to the black screen with letters and it says something about the x server, i had a problem with the x server with every version i installed and i dont know what to do, please help me, ive been asking alot of stuff about the x server and no1 can give me an accurate answer please tell me what do i NEED to download or do to end with this problem.

And someone told me that the alpha 4 i dont even know what the hell alpha 4 or 3 or 100 means but someone told me that that thing has problems with the newest video cards and that the new alpha 5 will support them.
A problem with an old card is impossible because my XPS is only a month old and it has one of the best and newest cards in the market. So as i said please help me with REAL ANSWERS.:confused:

Thanks.

Calm down. Try this thread instead. [http://ubuntuforums.org/showthread.php?t=563031&highlight=dell+XPS+m1730]("http://ubuntuforums.org/showthread.php?t=563031&highlight=dell+XPS+m1730")

---

