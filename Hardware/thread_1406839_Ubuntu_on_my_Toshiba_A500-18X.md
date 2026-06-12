---
title: "Ubuntu on my Toshiba A500-18X"
date: 2010-02-14
forum: Hardware
---

### Post by Mineiro on 2010-02-14
Hello,

I just got a new laptop for college, and I have found Ubuntu, which is installed on the institution's classrooms is superior to Windows in every programming related aspect.

I decided to install it on my laptop, and unfortunately a lot of stuff doesn't work out of the box:
-Can't set correct resolution (probably will be solved by installing nVidia drivers)
-WLAN card not detected
-Quick launch buttons not working

That's it for now. I'd like to ask for your help since I am not at all used to working with linux systems.

Thanks for your time :)

~Mineiro

---

### Post by Mineiro on 2010-02-14
Bump!

Another problem... I had 2 partitions on my HDD (one for windows + 1 for data) and I made  a 3rd one for ubuntu. And now I can't access the data partition from within Windows :S

---

### Post by Mineiro on 2010-02-15
Anyone?

---

### Post by kr0b1t on 2010-02-20
Could you please post the specs of your toshiba  and the version of Ubuntu ( 32 or 64 bits )

I have an A500-01x ( Canadian ) with the following specs:

```

Intel® Core™ i5-430M processor (2.26GHz, 3MB L3 Cache) with Intel® Turbo Boost technology
Standard Memory: 2GB + 2GB DDR3 (1066 MHz)
640GB (5400 RPM); Serial-ATA hard disk drive
NVIDIA GeForce® GT 330 (  1GB )
10/100/1000 integrated Ethernet LAN
Realtek Wireless LAN (802.11 bgn)
Integrated VGA Web Camera for Video over IP
Integrated microphone for Voice over IP

```

with Ubuntu 9.10 64 bits.

Mostly everything OK. Still working in wireless and speakers.

No problem with the nvidia drivers.

---

### Post by ancientrustic on 2010-02-20
You certainly need to install the nvidia driver.You should have been offered this when you first logged in.Otherwise go to System/Administration/Hardware Drivers. There will then be a search for drivers, install and reboot. If you have the newest Realtek wireless then you will probably need to install the drivers manually. If you have Realtek get back and I will post the details.

---

### Post by kr0b1t on 2010-02-20
I have a Realtek 8172 ( rev. 10 ):
```

# lspci -v | grep Network
07:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)

```

I'm trying to find a 64 bit drivers to compile and use.

---

### Post by kr0b1t on 2010-02-20
I followed [http://www.linwik.com/wiki/using+the+realtek+8172+and+8192se+wireless+controller+with+ubuntu+9.10](http://www.linwik.com/wiki/using+the+realtek+8172+and+8192se+wireless+controller+with+ubuntu+9.10)

is working at home :P

---

### Post by ancientrustic on 2010-02-21
You need the RTL8192SE drivers. Then follow the instructions on this page [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126?comments=all.You](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126?comments=all.You) will find the instructions about half way down this long page, posted by 'Wastedonanime  wrote on 2009-12-10:'. I have Toshiba laptop with this chip and I found I only needed to follow method 1 from the readme file in the RTL8192SE folder. Don't forget to reboot once you have done the installation. Good luck.

---

