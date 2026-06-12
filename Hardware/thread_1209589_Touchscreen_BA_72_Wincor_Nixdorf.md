---
title: "Touchscreen BA 72 Wincor Nixdorf"
date: 2009-07-10
forum: Hardware
---

### Post by benste on 2009-07-10
HI All I tried to use the xorg input packages for touch screens provided through APT, but none of them worked. I also tried some tutorials on the net like seeing where it is plugged in with cat /dev/ttyS0 and so on.

The screen is working fine as display, but I can't use it for touch in Ubuntu yet, as long as I tried every driver I'm not sure whether I have to config sth. manually after installing Xorg input drivers.

What can I do to get at minimum a seeable reaction that the PC is aware of the screen ?

---

### Post by crazybilly on 2010-02-21
I haven't tried them yet, but you might try this [driver page from Wincor]("http://www.wincor-nixdorf.com/internet/site_EN/EN/Support/Downloads/POSLotterySystems/Driver/Display/Display_node.html")

---

### Post by benste on 2010-02-22
HI, I've successfully installed the Touchscreen drivers but guess the main porblem still exists, possibly the screen isn't detected as it's attached through internal com ports.

I've tried to install the snx_golden module, but wasn't able to compile it.

---

### Post by benste on 2010-02-22
If there's still someone out who may help me, heres the log while "make install"

of
WN PCI COM board Linux driver - release 1.08
from [http://www.wincor-nixdorf.com/internet/site_EN/sid_177132DF7A0BEB9474234A66DDA53EA2.live1/EN/Support/Downloads/POSLotterySystems/Driver/MultiIO/MultiIO_node.html]("http://www.wincor-nixdorf.com/internet/site_EN/sid_177132DF7A0BEB9474234A66DDA53EA2.live1/EN/Support/Downloads/POSLotterySystems/Driver/MultiIO/MultiIO_node.html")

```
cd snxmknod;\
	./snxmknod
Build Golden tty file node (ttySNX0 ~ ttySNX31)
/dev/ttySNX0
/dev/ttySNX1
/dev/ttySNX2
/dev/ttySNX3
/dev/ttySNX4
/dev/ttySNX5
/dev/ttySNX6
/dev/ttySNX7
/dev/ttySNX8
/dev/ttySNX9
/dev/ttySNX10
/dev/ttySNX11
/dev/ttySNX12
/dev/ttySNX13
/dev/ttySNX14
/dev/ttySNX15
/dev/ttySNX16
/dev/ttySNX17
/dev/ttySNX18
/dev/ttySNX19
/dev/ttySNX20
/dev/ttySNX21
/dev/ttySNX22
/dev/ttySNX23
/dev/ttySNX24
/dev/ttySNX25
/dev/ttySNX26
/dev/ttySNX27
/dev/ttySNX28
/dev/ttySNX29
/dev/ttySNX30
/dev/ttySNX31
/dev/ttySNX32
cd snxdump;\
	make install
make[1]: Betrete Verzeichnis '/home/kasse/Desktop/WNPCICOMLinux_driver/golden/snxdump'
gcc -O2 -pipe -o snxdump snxdump.c	
cp -p snxdump /usr/bin
make[1]: Verlasse Verzeichnis '/home/kasse/Desktop/WNPCICOMLinux_driver/golden/snxdump'
cd snxterm;\
	make install
make[1]: Betrete Verzeichnis '/home/kasse/Desktop/WNPCICOMLinux_driver/golden/snxterm'
gcc     -c -o snxterm.o snxterm.c
make[1]: Verlasse Verzeichnis '/home/kasse/Desktop/WNPCICOMLinux_driver/golden/snxterm'
```

sry for the german log but it looks like the makefile was created in german too, if you need a translation of something don't worry to ask.

---

### Post by amuro on 2010-03-12
use egalax touchscreen driver for your BA72 wincor-nixdorf :
[http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm](http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm)

i use them and it work perfectly on : ubuntu and archlinux

---

### Post by benste on 2010-03-12
Sorry for the late reply, but I found out that it isnt a ttyS1 Problem,

problem was related to a wrong Xorg configuration.

I've posted a short how to on my blog how the touchscreen works with 9.04 and it's default mutouch drivers.

[http://benste.blogspot.com/2010/02/ba72a-wincor-nixdorf-touchscreen-serial.html]("http://benste.blogspot.com/2010/02/ba72a-wincor-nixdorf-touchscreen-serial.html")

---

