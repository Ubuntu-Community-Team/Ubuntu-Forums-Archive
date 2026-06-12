---
title: "Suspend a Toshiba A100"
date: 2007-10-14
forum: Hardware &amp; Laptops
---

### Post by devel3 on 2007-10-14
Hi I am new in Ubuntu and I have a problem with suspend to ram. I suspend the laptop but when I resume it the screen and the keyboard don't work. I have tried a lot of things whithout success.

The laptop is a Toshiba A100-999 with a Nvidia GeForce Go 7300 and the Ubuntu Feisty Fawn. The same problem in Gutsy Gibbon rc.

Thanks

---

### Post by benpage26 on 2008-02-14
I have a similar problem, when my laptop goes on standby.

It will wake up, ask for my password, and then suddenly go to a text only screen. then refuse to accept any input.  The text said something about a stack trace maybe?  i have a photo i could upload if that will help?

---

### Post by quantumnight on 2008-02-17
I don't know if this relevant at all, but I have a Dell i8600 that had a similar problem.  The solution was to open /etc/X11/xorg.conf and add

Option          "NvAGP"           "1"

in the section labeled Section "Device"

Hope this is helpful.

---

