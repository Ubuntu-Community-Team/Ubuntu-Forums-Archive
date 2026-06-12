---
title: "HP Laptop makes clicking sound sometimes"
date: 2013-08-04
forum: Hardware
---

### Post by bsamim on 2013-08-04
Hi, I am running ubuntu 13.04 64 bit on an HP Pavillion dv7 Im not sure if some linux process is running to cause this but sometimes the laptop will make a click sound for a second. I checked the temperature and the cores are cool using the program sensors. I am not seeing anything unusual in the system log. I am not sure what could be causing the issue. I don't remember this happening in the past. I did change the hard drive about a month ago with a brand new WD one so I don't think that should be a problem but you never know. Any ideas would be appreciated.

---

### Post by hansdown on 2013-08-04
Welcome to the forum, bsamim.

It's possible, that the WD hardrive is doing a read or write function, when the clicks happen.

---

### Post by thespirit3 on 2013-08-05
It's also possible the the HD is going into a power-save mode, parking the heads periodically.

Try this from the command line and see if it temporarily stops:-

sudo hdparm -B 255 /dev/sda

If so, you can add the above command (without the sudo) to /etc/rc.local.


Steve

---

### Post by bsamim on 2013-08-11
thanks I will give that a try

---

