---
title: "configure X"
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by hirohitosan on 2009-02-04
Hi there. I just installed Ubuntu on my computer. After installation it doesn't recognize my monitor and gr. card. How can I download and install NVidia, driver from terminal (since now I cannot use X)

I tried ```
$ sudo dpkg-reconfigure xserver-xorg
```
but all that I can configure in my keyboard. There are no options for monitor graphic card etc

do I have to add something else?

thanks

---

### Post by avtolle on 2009-02-04
Try booting at Recovery Mode (second option in Grub menu); IIRC, there will be some options listed there, one of which is to "fix X" (or something close to that). Select that, and see if that at least gets you to the desktop.

---

### Post by hirohitosan on 2009-02-04
> **avtolle said:**
> Try booting at Recovery Mode (second option in Grub menu); IIRC, there will be some options listed there, one of which is to "fix X" (or something close to that). Select that, and see if that at least gets you to the desktop.
well I cant. I chose recovery fix X and same ... cannot see nothing at my monitor just colored lines.

there no a way to set from console a lower resolution like 800x600 or 640x400?

---

### Post by glotz on 2009-02-04
There's something here, pretty vague though [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

