---
title: "Installing Image to USB drive"
date: 2009-09-30
forum: Installation &amp; Upgrades
---

### Post by teward on 2009-09-30
How long does it usually take for the image to be written to the USB drive?

I've been sitting here for an hour already, and it's becoming annoying.

---

### Post by earthpigg on 2009-09-30
im assuming it is a normal sized .img? 400mb-1gb?

much less than an hour. something went amiss.

are you using dd or some other tool?

---

### Post by teward on 2009-09-30
Got the .img from the Ubuntu download site, MIT Media Lab mirror, size approx. 980 MB.

The tool I'm using is ImageWriter, per the install instructions posted on the Ubuntu site.

**EDIT: The USB drive i'm writing the image to is a 2GB USB drive.  I'm assuming it wouldn't need more space than that, right? **

---

### Post by earthpigg on 2009-09-30
correct.

you can cancel that operation. if it was going to work, it would have worked by now.

i suggest one or both of the following:

-try a different thumb drive, from a different manufacturer.
-try a different tool, such as dd. be very careful with the dd command. [http://wiki.archlinux.org/index.php/Beginners_Guide#USB_stick](http://wiki.archlinux.org/index.php/Beginners_Guide#USB_stick) ...that one little apragraph about the "UNIX method" is what you want. will work with any linux distribution, any unix distribution, and any proper .img file.

---

### Post by teward on 2009-09-30
/resolved

It just finished after I cancelled and restarted the process.  It took some time (possibly because I wrote the image using a laptop?), but it finished.

:)

---

### Post by earthpigg on 2009-09-30
yay :D

be sure to mark the thread as 'solved', please. 'thread tools', at the top.

---

### Post by teward on 2009-09-30
Did I not already mark it as solved?

---

