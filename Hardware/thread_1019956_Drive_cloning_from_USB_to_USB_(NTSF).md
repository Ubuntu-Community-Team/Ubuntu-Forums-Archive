---
title: "Drive cloning from USB to USB (NTSF)"
date: 2008-12-23
forum: Hardware
---

### Post by fhsm on 2008-12-23
I have a bit of a strange problem.  I do the tech support for my family.  My mom is out of drive space on her XP Pro system (NTSF).  

What I’m hoping to do is use my Ubuntu 8.04 laptop to clone her hard drive onto a larger disk.  (Pull her drive, hook it up as a USB drive to my laptop, do the same with a new larger drive, clone her NTSF XP disk to the new one with a bit more breathing room.)

I’m good on the hardware part but I’ve had zero luck turning up something on the cloning front.  

Any chance someone can tell me if and if so how to do this with Ubuntu?

Thanks!

---

### Post by Aearenda on 2008-12-23
Take a look at ntfsclone, which is in the ntfsprogs package. But I'd use the Clonezilla LiveCD for this, and I'm sure there are others.

---

### Post by fhsm on 2009-01-04
Thanks for the tip.  I ended up cutting out a couple of steps and using [http://www.acronis.com/homecomputing/products/trueimage/](http://www.acronis.com/homecomputing/products/trueimage/) on the XP system.  The 15day free trial version worked just fine.

---

### Post by ssam on 2009-01-04
this can also be done with dd
[http://ubuntuforums.org/showthread.php?t=939854](http://ubuntuforums.org/showthread.php?t=939854)

---

### Post by Aearenda on 2009-01-04
dd is slow as it copies all the empty space too, but it is certain to create an exact copy!

---

