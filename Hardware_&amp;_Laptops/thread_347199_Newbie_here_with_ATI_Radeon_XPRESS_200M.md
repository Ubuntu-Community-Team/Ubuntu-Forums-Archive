---
title: "Newbie here with ATI Radeon XPRESS 200M"
date: 2007-01-26
forum: Hardware &amp; Laptops
---

### Post by greco_tux on 2007-01-26
Hey guys! Just installed ubuntu  6.10 on my Compaq R4000. The install went very smoothly, and I must say, this looks like a great distro. I was wondering how I could tell if I am using the right driver for my video card (ATI Radeon XPRESS 200M). I downloaded a driver from ATI (AMD)...

ati-driver-installer-8.32.5-x86.x86_64.run...

How do I go about installing it?

Also does it matter if I installed the i386 ubuntu on my laptop even though it's an athlon 64 ?

Any help would be greatly appreciated....

---

### Post by rmartz on 2007-01-27
I installed on my laptop with the xpress 200m without downloading any drivers. Seems to work fine for me so far.

Is it working for you?

---

### Post by firstc624 on 2007-01-27
this is how i c\got my 2oom xpress to work on my lappy.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b)


give it ia shot.  it worked best for me w/ a clean install

best luck

---

### Post by greco_tux on 2007-01-27
The install went smoothly, and yes it is working fine. I was just wondering if ubuntu was using some generic driver or if it was actually using the proprietary ATI/AMD driver. In other words, I would like to know if there is a differnce betwen these two drivers (if they are in fact different drivers that is)....

---

### Post by DerArzt on 2007-02-10
First of all, to check which driver you are using, open a terminal and type 
[HTML] sudo gedit /etc/X11/xorg.conf [/HTML]
scroll down to where it says Section "Device". If under driver it says "ati", you are using the generic driver. if it says fglrx you are using the driver you tried to install. 

That said, I would recommend using the 8.33 drivers, because those are the first drivers i have managed to get working in a stable manner. I also have an XPRESS 200M, and up until i installed the 8.33 drivers, I would get hard locks when trying to doing anything requiring 3d rendering, be it beryl, or a game. If you wish, you can install these using method 2 here:
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

---

