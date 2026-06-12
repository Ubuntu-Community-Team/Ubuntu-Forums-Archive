---
title: "Ubuntu cannot recognize old laptop's wireless card"
date: 2011-11-03
forum: Hardware
---

### Post by Oliverrayde on 2011-11-03
Hey guys!

Just to briefly say, I love linux and I love the originality that has arisen because of it.

To the problem. I have this old laptop that Ubuntu does not want to recognize its wireless card! It is on the inside of the device.

 I can't find the exact specs but if someone tells me how I will gladly post them! 

Thank you Linux community for the advanced help!

---

### Post by gordintoronto on 2011-11-03
If you mentioned the brand and model of laptop, that might be useful. Also the version of Ubuntu.

Open Terminal and enter this command: lspci

It should produce around a dozen lines of output, and one of them might include "802.11". That's your wireless adapter. Copy/paste that line into a message.

If it doesn't appear there, it might be a PCCard or USB device.

---

