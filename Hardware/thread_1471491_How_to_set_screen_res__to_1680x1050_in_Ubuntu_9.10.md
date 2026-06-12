---
title: "How to set screen res  to 1680x1050 in Ubuntu 9.10 and Asus K50IJ?"
date: 2010-05-03
forum: Hardware
---

### Post by vickoxy on 2010-05-03
Hi,
my friend is trying to connect his Samsung 206BW Monitor to Asus K50IJ Laptop, but there is no way that he get 1680x1050 res. The highest is 1366x768.

Any clue?

It is little bit hard to help him because we have contact only on skype. So, if anyone knows...


And, i saw some old Threads regarding xorg.conf, but there is no xorc.conf anymore in ubuntu 9.10. Is there some easy way to make this working...?

Asus K50ij: Pentium Dual-Core T4300 2x 2.10GHz • 3072MB (1x 1024MB und 1x 2048MB) • 320GB • DVD+/-RW DL • Intel GMA X4500M (IGP) 


Thanks

---

### Post by wmatthews on 2010-05-03
If I am not mistaken you have to change your /etc/X11/xorg.conf.

Vertical and Horizontal Sync values to what your monitor is.  Just look up your monitor and see what the value really is. Then restart X.

---

### Post by Yellow Pasque on 2010-05-03
If your friend has internet access, he should pastebin the X log: [http://ubuntu.pastebin.com/](http://ubuntu.pastebin.com/)

---

### Post by vickoxy on 2010-05-04
> **wmatthews said:**
> If I am not mistaken you have to change your /etc/X11/xorg.conf.

Vertical and Horizontal Sync values to what your monitor is.  Just look up your monitor and see what the value really is. Then restart X.

As said-he has no xorg.conf file. After Ubuntu 9.04 there is no xorg.conf file in /etc/X11/xorg.conf-you have to generate it, but i am not sure if he/i can do it this way...

---

### Post by vickoxy on 2010-05-04
Any idea?

---

### Post by vickoxy on 2010-05-05
Bump

---

### Post by dino99 on 2010-05-05
remove/purge the installed video driver then reinstall it, you may need to remove ALL these xserver-xorg- ... you dont need too, then:

sudo update-initramfs -u
sudo dpkg --configure -a

---

### Post by vickoxy on 2010-05-06
Ok, this is what he has. I don´t know if the re-installation of these drivers is enough. He use mint 8 (Ubuntu 9.10), but i suppose they are using same drivers...

Thanks

---

