---
title: "LiveCD parameters for resolution"
date: 2005-06-11
forum: Hardware &amp; Laptops
---

### Post by edmetric on 2005-06-11
I run an IBM S50 with Intel 3.0 P4. On LiveCD I only get 800x640 screen resolution. My monitor is Acer AL1913 on the motherboard controller. What parameter can I pass to boot to allow (any) increased resolution?  :smile:  It would make life better.

---

### Post by john_walsh54 on 2005-06-12
After initial boot type at the prompt:
 livecd xres=widthxheight

widthxheight is pixels, e.g. 1023x768. I have never tried this for Ubuntu, but it is a kernel parameter.

---

