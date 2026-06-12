---
title: "Drivers on Asus 1101ha"
date: 2009-09-29
forum: Hardware
---

### Post by miro.mannino on 2009-09-29
[B]I Use Ubuntu 9.04 with kernel 2.6.28-15


ETHERNET:[/B]

Download AR81Family-linux-v1.0.0.10.tar.gz from [http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx)


```
tar -xzvf AR81Family-linux-v1.0.0.10.tar.gz
cd src
make
sudo make install
sudo insmod atl1e.ko
```-------------------------------------------------------------------------------------------
[B]
WIRELESS:[/B]

Just Install linux backports:

```
sudo apt-get install linux-backports-modules-jaunty
```-------------------------------------------------------------------------------------------

**GMA500 GRAPHIC CARD:**

- add this software sources:

```
deb http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu jaunty main

```- open compiz settings with this command:

```
sudo priviledge /usr/bin/compiz
```- ensure that the WHITELIST have psb, like this:

```
# Driver whitelist
WHITELIST="psb nvidia intel ati radeon i810 fglrx"
```- install:


[LIST]
[*] psb-kernel-headers
[*] psb-firmware
[*] psb-kernel-source
[*] poulsbo-driver-3d
[*] xpsb-glx
[*] psb-modules
[*] poulsbo-driver-2d
[*] xserver-xorg-video-psb
[/LIST]

---

### Post by badook on 2009-09-29
Thanks a lot! Anyway is there any hope for having the hotkeys working? In particular the dim light is pretty important...

---

### Post by chilimac02 on 2009-09-30
thanks for posting a quick reference here for us 1101ha users. I got this thing a few months ago, but haven't been able to crack the GMA 500 problem as of yet. I'll give your instructions a go and see what I get.

---

### Post by Apopas on 2009-10-13
Thank you so much bro. After so many experiments, with your howto my netbook worked perfectly :)

---

