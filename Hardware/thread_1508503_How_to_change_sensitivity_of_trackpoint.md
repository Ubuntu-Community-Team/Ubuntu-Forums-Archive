---
title: "How to change sensitivity of trackpoint?"
date: 2010-06-13
forum: Hardware
---

### Post by wolfv6 on 2010-06-13
Is there a way to change the sensitivity of a trackpoint?  I am using a                            Lenovo ThinkPad USB Keyboard with TrackPoint Mfg Part #: 55Y9003 on Ubuntu 10.04.
[IMG]http://www.costcentral.com/product-images/I813656.jpg[/IMG]
Here is what I tried based on [Lowering Gaming Mouse Sensitivity in Ubuntu 10.04]("http://patrickmylund.com/blog/lowering-gaming-mouse-sensitivity-in-ubuntu-9-10/") (it didn't work):
```
$ xinput --list --short
 Lite-On Technology Corp. ThinkPad USB Keyboard with TrackPoint    id=10    [slave  pointer  (2)] 
 $ xinput --set-prop "Lite-On Technology Corp. ThinkPad USB Keyboard with TrackPoint" "Device Accel Constant Deceleration" 5 
 property Device Accel Constant Deceleration doesn't exist, you need to specify its type and format 
 
```Thank you.

---

