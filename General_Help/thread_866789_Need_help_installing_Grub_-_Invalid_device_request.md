---
title: "Need help installing Grub - Invalid device requested"
date: 2008-07-22
forum: General Help
---

### Post by Shunsuke_01 on 2008-07-22
I am following a guide to install Grub as I have reinstalled Windows XP and it no longer appears. 

I type "find /boot/grub/stage1" which gives me "hd0,5" or something.

The next step (if I am correct) is grub> root (hd0,5). No problems yet.

But then when I type "grub> setup (hd0) it says "invalid device requested".


How can I fix this? Is there a way or should I just reinstall Ubuntu (it would be a bit of a hassle though)? :confused:

---

### Post by dracayr on 2008-07-22
type

grub> setup (hd

and then press tab. There should be options presented to you.

dracayr

---

### Post by AndyCee on 2008-07-22
Is this the guide you're using:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

have you missed this step?
```
grub> root (hd0,5)
```

I have subscribed to this thread, as it has saved my wife's Vista partition on 3 occasions.

---

