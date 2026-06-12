---
title: "Older Geforce GPUs ---&gt; CUDA support. How?"
date: 2018-03-16
forum: Hardware
---

### Post by slim6y on 2018-03-16
Hello,

I have an old Alienware Mx17 R2 which I decided to ditch Windows (wasn't working anyway) and replace with the latest Ubuntu. So far so good, but I a very much stuck with the drivers. 

I want to install the CUDA drivers that are available on the nVidia site, but these just do not seem to work. Does anyone have a step by step how to?

The cards are a GT(X?) 240m and a GT9400, both are compatible with CUDA. 

I am at a fresh and clean install of Ubuntu and updated. But the driver version loaded here *other than the noveau) is 340.104 yet nVidia have a later version 340.106 which I also can not install. 

My main issue is I don't yet understand the Terminal functions. It is all new to me. 

Thank you for your help in advance.

---

### Post by Yellow Pasque on 2018-03-16
You should use the driver that is available in the Ubuntu repo. The CUDA driver comes as part of that (libcuda1-340).
Beware that you are using "legacy" CUDA devices with limited compute abilities and they will only work with older CUDA toolkits (6.5)

---

