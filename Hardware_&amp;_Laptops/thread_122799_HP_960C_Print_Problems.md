---
title: "HP 960C Print Problems"
date: 2006-01-28
forum: Hardware &amp; Laptops
---

### Post by firekat on 2006-01-28
I have installed a HP960C and at first it appears to print ok but after looking at it more carefully I notice that The bottom and sides are not printing properly.

I have the latest hplip loaded, and since I am new I also noticed that this is a "base" program and does not have all the bells and whistles that would be available with the full on hplip.  I have searched far and wide to find this package for Ubuntu - to no avail.  I would hope that having the full version I would be able to fix this problem as it has calibration and maintenance functions.  There is supposedly command line stuff available hplip-utils I think it is but I tried sudo hplips-utils.  Nothing.  Could not find any documentation on it either.

I found in some documentation in the installed package the following:

> Issue 4: When printing Letter media, the bottom row is printed incompletely.
Solution:
Some applications use enscript for printing, make the following changes to /etc/enscript.conf. This tip came from Patricio Paez.

from:

DefaultMedia = Letter

to:

DefaultMedia = Letterdj


I searched my system for this file and did not find it so I am assuming this would not be the correct fix.

Does anyone know how th fix my problem or get the full on hplip program?

Trying my best to do as much of this on my own.  Fixed a problem with a video adapter by reading the faq for ubuntu.  When all else fails read the manual right?  Could not find anything for this printing issue or anything on my M Audio Audiophile 2496 card either.

Thanks in advance!

---

