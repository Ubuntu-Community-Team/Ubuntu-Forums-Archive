---
title: "Minimum video memory"
date: 2005-01-25
forum: Hardware &amp; Laptops
---

### Post by tleroy on 2005-01-25
Simple question, I hope.  Where can I find the minimum video card memory requirements for running Ubuntu Linux in Graphic mode?  I have a Rage IIc video card with 8 MB of ram!  Pretty old, I know.

---

### Post by az on 2005-01-26
I have Ubuntu on an old computer with a 1 meg video card.

That will only impact on your maximum color depth and resolution.  On my card, I cannot do more than 800x600 in 15-bit color.

You typically can do 1024x768 in 24-bit color on an 8MB card...  If it does not work, try going down on the color depth as opposed to the resolution:

sudo dpkg-reconfigure xserver-xfree86

---

### Post by tleroy on 2005-01-26
Thanks Azz!

---

