---
title: "Intel GMA 3000 resolution?"
date: 2007-07-12
forum: Hardware &amp; Laptops
---

### Post by pvangarde on 2007-07-12
The Intel IGP GMA 3000 (not X3000) should support a resolution of 1440x900. The Xfree driver reports (in the xorg.log)  "modes supported" up to 1280x1024 and "future modes supported"(???)  that include 1440x900. However, I can only get as high as 1280x1024 and it looks stretched on my wide screen :(. How can I remedy this? I understand I can download intel drivers from their website, would that help?

FYI: Changing the mode to 1440x900 in xorg conf file did not do it

---

### Post by bdtgp on 2007-07-12
This is almost always a video card issue so if you know how to install the drivers correctly then try it.  I would check to see if there are any Intel drivers in the Synaptics first though because then you know Ubuntu supports them.

---

