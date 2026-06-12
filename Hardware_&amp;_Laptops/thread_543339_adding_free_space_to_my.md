---
title: "adding free space to my /"
date: 2007-09-05
forum: Hardware &amp; Laptops
---

### Post by darkhacker902 on 2007-09-05
Ok heres what Im working with.

I decided to make an 11Gb Partition here, thinking that I wouldnt use ubuntu that much. Well, Im using it every day, and Almost never touch windows. I have a 160 Gb hard drive.

115 GBs= Windows vista.

9 GBS recovery drive in vista.

11Gbs Ubuntu

2Gbs Swap.

11 Gbs of free space.


Now, when I boot into knoppix to use QTparted, I get an error when I try and resize my windows partition, so i can have around 50 or 60 more gigs in ubuntu.
The error says something about me not having shut down windows properly, but when I restart, It gives me the same crap.

Well I managed to grab around 11Gbs free space using vista's Partion editor, and Want to put that on my / And hopefully more. 

BUT once again, When I go to QTparted, under my /hda3 partition (where ubuntu is) all the options are shaded :(.

And It wont let me do it inside ubuntu either.

So What do I do?

---

### Post by merlinus on 2007-09-05
Use gparted live cd:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

