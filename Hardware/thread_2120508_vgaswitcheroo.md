---
title: "vgaswitcheroo"
date: 2013-02-26
forum: Hardware
---

### Post by Anden100 on 2013-02-26
Hi all,

So, i finally decided to get Ubuntu up and running on my laptop, but i am having some quite annoying issues with the AMD Switchable graphics.

The GPU is an 5470M, so it is not supported by the official drivers, hence i will need to use vgaswitcheroo, which works perfectly fine for switching off the discrete gpu (which is more or less all i need).

However, i have to give the user access to /sys/kernel/debug every time, to avoid "Permission: Denied" issues everytime i attempt to turn off the GPU.

For now, i am running the following commands, whenever i boot my computer:
```
sudo su
chmod -R 705 /sys/kernel/debug
chown user:user /sys/kernel/debug/switcheroo/switch
exit
echo OFF > /sys/kernel/debug/switcheroo/switch
```

There are however two issues with this. Firstly, it is annoying to run 5 commands, whenever i wish to turn off the GPU (every boot). Is there any way to automate this? Secondly, granting the user access the the kernel directory like that isn't exactly... great...

Thank you in advance
Anden100

---

