---
title: "Switch video card"
date: 2013-06-08
forum: Hardware
---

### Post by printfede on 2013-06-08
I'm running Ubuntu on my Asus K95V which has two graphics card:
```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [GeForce GT 630M] (rev ff)

```

How do I find out which one is being used at the moment and how can I switch between them? Also I'm not sure if I should use Bumblebee.
Thanks for any help.

---

### Post by Yellow Pasque on 2013-06-08
With Optimus, they're both powered on, but only the intel is being used. Yes, you want to use bumblebee: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by printfede on 2013-06-13
Thank you Temüjin. I run glxgears with optirun and the difference is evident. Now, what do I have to do if I want nvidia card to be used by default by all applications?

---

### Post by Yellow Pasque on 2013-06-13
> Now, what do I have to do if I want nvidia card to be used by default by all applications? 
Not recommended.

---

### Post by printfede on 2013-06-14
> **Temüjin said:**
> Not recommended.
Why?

---

### Post by Yellow Pasque on 2013-06-14
[http://ubuntuforums.org/showthread.php?t=2152186&p=12684841#post12684841](http://ubuntuforums.org/showthread.php?t=2152186&p=12684841#post12684841)

---

### Post by printfede on 2013-06-15
Thank you very much.

---

