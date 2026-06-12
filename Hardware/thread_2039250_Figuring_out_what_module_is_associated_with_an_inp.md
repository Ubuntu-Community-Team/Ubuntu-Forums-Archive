---
title: "Figuring out what module is associated with an input device, specifically js0"
date: 2012-08-08
forum: Hardware
---

### Post by timsloane on 2012-08-08
Hello all,

I have what I think is a simple question, though my Google-fu is failing on this one.  Given an input device in /dev/input (for instance, the joystick js0, which is my primary interest), how do I find out what module is being used for that device?  

I thought I could do an lsmod before and after plugging in the device and diff the results, but in this instance there was do difference.  However, a jstest did confirm that the joystick was indeed working.

---

