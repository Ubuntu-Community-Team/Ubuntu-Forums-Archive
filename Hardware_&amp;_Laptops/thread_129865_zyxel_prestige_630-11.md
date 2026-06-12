---
title: "zyxel prestige 630-11"
date: 2006-02-14
forum: Hardware &amp; Laptops
---

### Post by snot on 2006-02-14
I am new in linux and recently tried ubuntu. The problem is that I cannot figure out how to install the amedyn drivers for zyxel prestige 630-11. I have recently installed on mandriva but in ubuntu I can't use the internet and therefore apt-get. To install amedyn the following packages must be installed;
kernel-source
ppp
libpcap0 (also called libpcap ;) )
ppp-pppoatm 
libusb
libusb-dev
linux-atm 
Is there a way to install them without being online?

---

### Post by bernardfrancois on 2006-03-15
You could try to find the binary packages (on a computer with internet) and move them to your computer...
I guess you can use **apt-get** to download packages without installing them. Check **man apt-get** or **info apt-get** for more information.

---

### Post by mips on 2006-03-15
Might wanna check if the packages are on the CD, add the cd to your sources list I think is the way to do it.

Alternatively take your computer somewhere where you can get online via ethernet.

---

