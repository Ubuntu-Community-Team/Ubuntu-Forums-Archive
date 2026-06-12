---
title: "Jaunty boot-up freeze dialog box- please help- image included"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by pjhudson on 2009-04-25
I have the following issue after upgrading to jaunty from 8.10--  this is after the splash screen-- the problem along with this is that it is also frozen so the mouse, keyboard, nothing works and I have to force quit-

[IMG]http://farm4.static.flickr.com/3632/3473554296_1ef99354cf.jpg[/IMG]

I'm using a Toshiba Satellite A210 laptop with the mobile intel 945 express chipset display adaptor-

I tried recovery mode, which works, however, when I do the dpckg thing it says it has to download 100 some odd mb but then it just doesn't do it, I think it doesn't have an internet connection, maybe the wireless isn't working in recovery mode.   what can I do-- I would rather be able to fix this so I can use it rather than re-install from a clean slate.

---

### Post by edm1 on 2009-04-25
not too sure if this will help but have you tried booting into recovery mode (from the grub boot menu when you first start the computer) and reconfiguring xorg, there should be an option for it otherwise type:

```
dpkg-reconfigure xserver-xorg
```

---

### Post by pjhudson on 2009-04-25
I just tried it and it didn't work-- although I'm not sure I really changed anything in the configuration-- basically just said no, no, and left everything else blank

---

