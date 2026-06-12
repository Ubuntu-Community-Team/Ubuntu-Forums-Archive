---
title: "problems with video resolution"
date: 2005-12-15
forum: Hardware &amp; Laptops
---

### Post by jadams on 2005-12-15
I am having a bit of a problem changing to any resolution above 800x600. I have an onboard cirrus logic gd5480 video card hooked into a KDS VS-7 monitor. ANyone have any ideas how to get this to work? I have attached my xorg.conf file if anyone wants to take a look.

---

### Post by mlomker on 2005-12-15
Check your /var/log/Xorg.0.log for errors.  What I've seen in the past is that the onboard VGA cards won't do high resolution unless you lower the color depth--not enough memory on the card.

---

### Post by jadams on 2005-12-16
Thanks. I ended up setting the default color depth to 16-bit and that seemed to do the trick.

---

