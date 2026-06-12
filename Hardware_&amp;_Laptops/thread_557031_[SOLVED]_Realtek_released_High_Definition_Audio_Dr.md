---
title: "[SOLVED] Realtek released High Definition Audio Drivers for No Sound problem"
date: 2007-09-22
forum: Hardware &amp; Laptops
---

### Post by aldeby on 2007-09-22
This is just to point out that Realtek has released drivers for it **High Definition Audio Chipset.**
These are useful for all those that cannot hear anything from their laptop speakers (such as owners of HP pavilion dv9000 dv6000 dv2000 laptops, and all Intel ICH8 (Centrino) platform in general).

They are available here: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#2]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#2")

Note that in this forum you can find another working procedure that involves installing latest alsa drivers by hand, Realtek drivers cover the same points (and actually install latest alsa drivers), however they **come with an integrated automated installer **that eases things a lot. 

Happy Ubuntu! 
:popcorn:

---

### Post by thehkv on 2008-07-07
In readme it says

> Manual install:
Step 1. unzip source code
        tar xfvj alsa-driver-1.0.xx.tar.bz2

Step 2. Turn on sound support (soundcore module, default turn on)

Step 3. Complied source code
	a. cd alsa-driver-1.0.xx
	b. ./configure
	c. make
	d. make install
	e. ./snddevices

I'm stuck at 3b> 
hkv@hkv-desktop:~/Desktop/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

---

