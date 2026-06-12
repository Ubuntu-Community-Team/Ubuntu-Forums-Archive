---
title: "help me pls: Silicon Integrated Systems [SiS] 671MX"
date: 2010-05-10
forum: Hardware
---

### Post by jinsujais on 2010-05-10
hi..


I'm using ubuntu 9.10. I cant change my screen resolution.. The maximum resolution is stuck in 800*600. I want to change it to 1024*768.
I dont know more about Ubuntu. From internet, i found "lspci" command to check my graphics card. Its details are as follows:

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 SATA controller: Silicon Integrated Systems [SiS] AHCI IDE Controller (0106) (rev 03)
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

---

### Post by mhgsys on 2010-05-10
[http://go2.wordpress.com/?id=725X1342&site=ubuntuway.wordpress.com&url=http%3A%2F%2Fnacho.larrateguy.com.ar%2Fwp-content%2Fuploads%2F2009%2F07%2Fxorg-driver-sisimedia_0.9-1_i386.deb](http://go2.wordpress.com/?id=725X1342&site=ubuntuway.wordpress.com&url=http%3A%2F%2Fnacho.larrateguy.com.ar%2Fwp-content%2Fuploads%2F2009%2F07%2Fxorg-driver-sisimedia_0.9-1_i386.deb)


There ya go;
install this deb package and reboot.

if it doesn't work out for you have a look at page 28/29/etc in the link below

also; bookmark this >most active sis thread right here;[http://ubuntuforums.org/showthread.php?t=958967](http://ubuntuforums.org/showthread.php?t=958967)

(we're on page 45... having the sis 771/671 working on ubuntu 10.04 since page 38, and @purct even created modified drivers  to support  ASUS Widescreen Laptops - (specifically written for the X5DC but also may support others.)

---

### Post by gannite6364 on 2010-05-10
I wish they had one that works for lucid lynx 10.4, as that is the simple way.

---

### Post by mhgsys on 2010-05-10
**@gannite6364**

Read a little closer.

As I said; we're on page 45... **having the sis 771/671 working on ubuntu 10.04 since page 38**, and @purct even created modified drivers to support ASUS Widescreen Laptops - (specifically written for the X5DC but also may support others.) 

So...
Here ya go' ; a "howto" for sis 771/671 on ubuntu 10.04
[http://ubuntuforums.org/showthread.php?t=958967&page=38](http://ubuntuforums.org/showthread.php?t=958967&page=38)

---

### Post by jinsujais on 2010-05-11
thanks a lot... It works perfectly...

---

### Post by mhgsys on 2010-05-11
> **jinsujais said:**
> thanks a lot... It works perfectly...

Nice' 


Bookmark this thread for it will come in handy in the future;
[http://ubuntuforums.org/showthread.php?t=958967&page=45](http://ubuntuforums.org/showthread.php?t=958967&page=45)

it contains a "guide" on how to get the sis 771/671 running in 10.04 + modified drivers @purct created for asus laptops.

Also; it's the most active sis 771 671 thread since 2008 , containing lot's of contributing users.

---

### Post by jinsujais on 2010-05-11
> **mhgsys said:**
>  


Bookmark this thread for it will come in handy in the future;
[http://ubuntuforums.org/showthread.php?t=958967&page=45](http://ubuntuforums.org/showthread.php?t=958967&page=45)

it contains a "guide" on how to get the sis 771/671 running in 10.04 + modified drivers @purct created for asus laptops.
.

Thanks again... I'm planning to upgrade 9.10 to 10.04.. Thanks a lot..:)

---

### Post by mhgsys on 2010-05-11
You're absolutely welcome.

---

### Post by materialsmonkey on 2010-07-10
> **mhgsys said:**
> [http://go2.wordpress.com/?id=725X1342&site=ubuntuway.wordpress.com&url=http%3A%2F%2Fnacho.larrateguy.com.ar%2Fwp-content%2Fuploads%2F2009%2F07%2Fxorg-driver-sisimedia_0.9-1_i386.deb](http://go2.wordpress.com/?id=725X1342&site=ubuntuway.wordpress.com&url=http%3A%2F%2Fnacho.larrateguy.com.ar%2Fwp-content%2Fuploads%2F2009%2F07%2Fxorg-driver-sisimedia_0.9-1_i386.deb)


There ya go;
install this deb package and reboot.

if it doesn't work out for you have a look at page 28/29/etc in the link below

also; bookmark this >most active sis thread right here;[http://ubuntuforums.org/showthread.php?t=958967](http://ubuntuforums.org/showthread.php?t=958967)

(we're on page 45... having the sis 771/671 working on ubuntu 10.04 since page 38, and @purct even created modified drivers  to support  ASUS Widescreen Laptops - (specifically written for the X5DC but also may support others.)

I'm brand-new to all this and followed the instruction on pg45 & they worked perfectly, thanks!

---

### Post by mhgsys on 2010-07-10
[quote=materialsmonkey]I'm brand-new to all this and followed the instruction on pg45 & they worked perfectly, thanks![/quote]

Nice!

I'm happy to see my little "howto" still has use  (for people booting 10.04.)

---

