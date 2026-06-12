---
title: "Brother DCP 8045N bug with Intrepid Ibex"
date: 2008-11-18
forum: Hardware
---

### Post by thxbb12 on 2008-11-18
Hello all,

I've been a pretty happy user of Hardy with my Brother DCP-7045N laser printer. It was detected fine, cups used the DCP-7025 driver and it worked just flawlessly (I guess the 7025 and 7045 are very similar driver-wise).

A few days ago, I decided to upgrade to Intrepid.  The updgrade went well with no major problem.
However, since the upgrade everything I print is majorly shifted up and right. Basically, it prints about 5cm too high and 2cm too much to the left. Cups ignores all of my global printer margin settings.
This issue basically makes printing on Intrepid unusable as far as I'm concerned.
I then decided to do a fresh install from the CD, thinking it may have been an upgrade bug/issue.  Unfortunately it didn't make any difference.  I then tried KUbuntu 8.10 without any luck either.
Then I compared the driver used by cups in Intrepid with the one used in Hardy. They are exactly the same!  Therefore I can only conclude the problem resides at a different level: maybe the cups libraries ?  Not sure, because I can't use Ibex with the cups system from Hardy because they were way too many changes in this area.
I searched everywhere to see if someone got the same issue, but I haven't found one single person with the same issue (that Brother DCP-7045N doesn't seem very popular).
I think I'll have to revert to Hardy which I really want to avoid, but it seems I won't have any other choice :(

Any help would be *greatly* appreciated.  Thank you.
Florent

---

### Post by Sef on 2008-11-18
Moved to Hardware and Laptops.

---

### Post by thxbb12 on 2008-11-26
Anyone?? ... or am I the only to have encountered this?

---

### Post by rhu on 2008-11-28
Hi, I can confirm I get the same problem on Intrepid. 

I've been delving into the ppd driver provided by Brother (yes, you are correct it is listed as 7025, but this makes no difference).

I even copied (and modified) the 7045N mac osx ppd to work on intrepid (it actually gives you a few more options, such as toner save & reduce paper curl) to see if that was the problem - there were minor differences in the margin settings, but this was not significant.

Also I looked at the script /usr/local/Brother/lpd/psconvert2 and tried altering the shift_x_point and shift_y_point both to zero (which looked like it was the culprit), but no joy.

Seems like there are problems with margin offsets generally with intrepid:

[https://bugs.launchpad.net/ubuntu/+source/foomatic-db-hpijs/+bug/282186/](https://bugs.launchpad.net/ubuntu/+source/foomatic-db-hpijs/+bug/282186/)

---

### Post by ghed on 2010-02-04
Same problem on Ubuntu 9.10

---

