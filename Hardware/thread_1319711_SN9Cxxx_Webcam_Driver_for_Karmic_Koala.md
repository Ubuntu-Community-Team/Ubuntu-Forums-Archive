---
title: "SN9Cxxx Webcam Driver for Karmic Koala?"
date: 2009-11-08
forum: Hardware
---

### Post by SuperMetroid on 2009-11-08
Hi. I have a Microsoft Lifecam VX-3000 (a SN9C105r-based cam) and am looking for drivers for it for Ubuntu 9.10 Karmic Koala. 

The Video4Linux drivers appear to only be available for Ubuntu 7.04 Feisty and 7.10 Gutsy (as seen here: [http://www.linux-projects.org/modules/mydownloads/viewcat.php?cid=7](http://www.linux-projects.org/modules/mydownloads/viewcat.php?cid=7)).

Also, the Sonix SN9C102-based driver doesn't look like it would support SN9C105 (as per the name).

If there is someone out there using Karmic Koala with a working Lifecam, please share how you got it to work -- it would be greatly appreciated!

---

### Post by MasterPoulos89 on 2009-11-10
Just download and install the latest kernel. Worked for me....even in Karmic.

Here is the site: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

I will confirm kernel 2.6.32-r6 works for my lifecam-vx3000 in Karmic.

Hope this helps.

---

### Post by SuperMetroid on 2009-11-10
Thanks for the quick response! Yay, getting the latest kernel made it so my webcam's video worked! :KS However, the mic still doesn't work for me. Does yours?

---

### Post by MasterPoulos89 on 2009-11-10
Nope.....That is the best you can expect for now.

In the future it may work for the mic and may give better color quality. You need an external mic for now.

My color quality is ok but if your quality is the same as mine don't think thats the best linux can do. It is this particular cam and maybe some others that are not yet fully supported.

Microsoft obviously does not like to share their code.

At least it gives a decent picture though.

---

