---
title: "Any luck with Lenovo IdeaPad Y570?"
date: 2012-06-23
forum: Hardware
---

### Post by khughitt on 2012-06-23
Anyone running Linux on an Lenovo IdeaPad Y570? It looks like a really good hardware setup, but after searching the web some it looks like people have been having issues with the NVIDIA GeForce GT 555M that is ships with.

Anyone able to get it working properly, or know if this is likely to change in the near future?

Thanks!

---

### Post by TraBruno on 2012-07-02
I would like to know this too actually, anyone?

---

### Post by davidbilla on 2012-09-08
I have been running Ubuntu 12.04 on Lenovo Y570 since it's release. It all works fine.

You can get GT555M working with nvidia drivers using bumblebee and bbswitch. Once installed, you'll have to run your graphics intensive program with optirun. For eg.,

$ optirun glxspheres

In my laptop there is ~60 times speedup of glxspheres when run with optirun!

---

