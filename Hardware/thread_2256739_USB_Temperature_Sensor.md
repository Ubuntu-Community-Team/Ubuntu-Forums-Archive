---
title: "USB Temperature Sensor"
date: 2014-12-14
forum: Hardware
---

### Post by bilkay on 2014-12-14
I got a TEMPer USB temperature sensor (sold under the name eBest) on Amazon, and it said it's Linux compatible, but nothing was provided to make it work on Linux, and there weren't any instructions on how to. After a bit of digging, here's what I found:

First, download [http://toshiokk.dip.jp:8008/pcsensor-1.0.3.tgz](http://toshiokk.dip.jp:8008/pcsensor-1.0.3.tgz)

$ cd Downloads # or wherever your downloads go
$ tar -xf pcsensor-1.0.3.tgz
$ cd pcsensor-1.0.3
$ sudo -i
$ apt-get install libusb-dev # Run this if you get an an error telling you usb.h not found
$ make clean && make && make install && make rules-install
$ exit
$ # Insert device in usb slot
$ pcsensor
 69.12F 20.62C

It worked on 12.04 and 14.04

---

