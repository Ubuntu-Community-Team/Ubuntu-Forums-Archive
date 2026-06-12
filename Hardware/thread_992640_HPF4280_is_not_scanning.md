---
title: "HPF4280 is not scanning"
date: 2008-11-24
forum: Hardware
---

### Post by absolutezero1287 on 2008-11-24
I have an HP Deskjet F4280 and it prints just fine but I can't get it to scan. I try pressing the scan button and nothing happens. I use Xsane and it doesn't detect it.

---

### Post by GrahamM on 2008-12-17
> **absolutezero1287 said:**
> I have an HP Deskjet F4280 and it prints just fine but I can't get it to scan. I try pressing the scan button and nothing happens. I use Xsane and it doesn't detect it.

I have a Deskjet 4180. It prints fine and I think I have the right driver. I can scan from Xsane, but the scan button dies nothing. Mind you, in W2K, it does nothing either because HP don't have a driver for W2K. In XP, it does work if the full software install is done. But, this software seemed buggy and that is why I now have my wife's printer ;)

No big problem, but it would be nice to get the button working. Probably need HP software?

---

### Post by theozzlives on 2008-12-17
I have an Epson Stylus CX8400  that for the life of me couldn't get the scanner to work until I installed Alpha 1 of Jaunty Jackalope, but it's in Alpha so I don't recommend it. For now try:
```
sudo apt-get install libsane-extras
```
See if that works for you.

---

### Post by absolutezero1287 on 2008-12-18
I have the libsane-extras installed. :(
This is really annoying. I don't scan much but it would still be nice for it to work.

---

