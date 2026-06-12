---
title: "Canon LiDE 210 scanner in Ubuntu 12.04"
date: 2012-07-03
forum: Hardware
---

### Post by forkandles on 2012-07-03
Success with a Canon scanner in Ubuntu!! What???
Just amazing, given the history of Canon drivers and Linux.

For the benefit of anybody who has not been able to get their Canon LiDE 210 working in Ubuntu 12.04, here is what you do.

With scanner disconnected:
In Synaptic
Install  xsane 

OR 
In Terminal:
sudo apt-get install xsane

NB   libsane is already installed in 12.04. If you are using an earlier version of Ubuntu, you may also need to install libsane.

Connect scanner via USB port and start xsane using:
Applications > Graphics > xsane

---

### Post by rt82609 on 2012-07-23
I was able to get a scan to take place on my Canon scanner, but the image was very dark.  Is there an extra step to take in order to make the whites whiter?

---

### Post by forkandles on 2012-08-15
Initially I had the same problem with the first couple of scans, but things soon settled down and everything was fine.
The scanner may need to warm up fully.

---

### Post by headlessspider on 2012-09-22
yup. the scanner works with 12.04 with xsane

---

### Post by pdc on 2012-09-22
Canon LiDE 210 scanner

> the scanner works with 12.04 with xsane

> Success with a Canon scanner in Ubuntu

........*this is not entirely surprising*...........

as 

[http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON)

shows 

> [COLOR="Red"]CanoScan LiDE 210[/COLOR] USB [COLOR="Green"]Complete Support[/COLOR]

---

### Post by thotz on 2012-10-01
Hey, can somebody confirm this bug [https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/996741?](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/996741?)

---

