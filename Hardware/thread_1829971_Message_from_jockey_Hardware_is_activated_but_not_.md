---
title: "Message from jockey: Hardware is activated but not currently in use."
date: 2011-08-21
forum: Hardware
---

### Post by tingxyu1996 on 2011-08-21
Hello there!

I met a problem about Nvidia graphic card driver works in my Ubuntu 11.04.

Last time I installed Nvidia driver through jockey instanly, it says "Hardware is activated but not currently in use". I worried about it and then I search the problem with Google.

I found many of them also met the same problem with me, but finally they solved the problem by re-installing the driver. So, I re-installed it, but the same message again!

I try un-install and re-installing again and again(about 5 times), and restart. But the same message always appear in jockey.

So, I gonna ask 2 questions:
1) If it comes out the message like this, does it means the driver is not work properly?
2) How to solve this problem? I had try many method of 'them'(resolver and helper) given but still can't solve this message.

Help please? Your help will be appreciated!

---

### Post by realzippy on 2011-08-21
It might be a bug.
Check if your driver works and ignore it.
If nvidia-setting works and shows your monitor aso,everything is ok.

---

### Post by coffeecat on 2011-08-21
> **realzippy said:**
> It might be a bug.

It is a bug. :)

@tingxyu1996, if I remember correctly the message is actually "the driver is activated and not in use", not "hardware". If the driver is activated, it **is** in use. The message is a bug. If your system is working and you are getting the Unity desktop in 11.04 then your nvidia driver and card are working just fine.

---

### Post by dino99 on 2011-08-21
[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788)

---

