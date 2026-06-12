---
title: "undervolting howto: building kernel problem"
date: 2006-11-14
forum: Hardware &amp; Laptops
---

### Post by elfische on 2006-11-14
Hi,

to increase the battery live of my benq 5100u notebook I followed the undervolting howto of the wiki.
I downloaded the linux sources version 2.6.17-10 with
```
apt-get source linux-image-2.6.17-10-generic
```
and go step by step without any errors. 
But the command
```
AUTOBUILD=1 fakeroot debian/rules binary-debs flavours=generic
```
runs into the error:
```
dpkg-gencontrol -isp -DArchitecture=i386 -plinux-headers-2.6.17-10-38e \
                                          -P/home/elfi/undervolt/linux-source-2.6.17-2.6.17/debian/build/linux-source-2.6.17/debian/linux-headers-2.6.17-10-38e/
dpkg-gencontrol: error: package linux-headers-2.6.17-10-38e not in control info
make[2]: *** [debian/linux-headers-2.6.17-10-38e] Fehler 255
make[2]: Verlasse Verzeichnis '/home/elfi/undervolt/linux-source-2.6.17-2.6.17/debian/build/linux-source-2.6.17'
make[1]: *** [binary/linux-headers-2.6.17-10-38e] Fehler 2
make[1]: Verlasse Verzeichnis '/home/elfi/undervolt/linux-source-2.6.17-2.6.17/debian/build/linux-source-2.6.17'
make: *** [binary-debs] Fehler 2 
```

I have no idea what to do.
The line ```
plinux-headers-2.6.17-10-**38e **\
```
is different in the bold part on every run I did.

Bye
Elli

ps: sorry for my english. I am a little bit out of training.

---

### Post by jmmwc on 2006-11-14
hi,

try this howto: [http://doc.gwos.org/index.php/Kernel_Compilation]("http://doc.gwos.org/index.php/Kernel_Compilation")

---

### Post by woifi on 2006-12-06
hi!

> **elfische said:**
> 
But the command
```
AUTOBUILD=1 fakeroot debian/rules binary-debs flavours=generic
```
runs into the error:
```
dpkg-gencontrol -isp -DArchitecture=i386 -plinux-headers-2.6.17-10-38e \
                                          -P/home/elfi/undervolt/linux-source-2.6.17-2.6.17/debian/build/linux-source-2.6.17/debian/linux-headers-2.6.17-10-38e/
dpkg-gencontrol: error: package linux-headers-2.6.17-10-38e not in control info
make[2]: *** [debian/linux-headers-2.6.17-10-38e] Fehler 255
make[2]: Verlasse Verzeichnis '/home/elfi/undervolt/linux-source-2.6.17-2.6.17/debian/build/linux-source-2.6.17'
make[1]: *** [binary/linux-headers-2.6.17-10-38e] Fehler 2
make[1]: Verlasse Verzeichnis '/home/elfi/undervolt/linux-source-2.6.17-2.6.17/debian/build/linux-source-2.6.17'
make: *** [binary-debs] Fehler 2 
```

I have no idea what to do.
The line ```
plinux-headers-2.6.17-10-**38e **\
```
is different in the bold part on every run I did.

same problems here! i'm not familiar with this way of compiling a kernel, but it seems quite interesting. any solutions out there?

the bold part is indeed random, as mentioned in the wiki> When the build is ready, install it on your system. Replace xxxx. This is a random string..

bye

woifi

---

