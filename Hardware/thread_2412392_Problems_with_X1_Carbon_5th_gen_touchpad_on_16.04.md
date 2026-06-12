---
title: "Problems with X1 Carbon 5th gen touchpad on 16.04"
date: 2019-02-12
forum: Hardware
---

### Post by berserq0123 on 2019-02-12
I have faced with some strange behaviour of the touchpad on 16.04
Sometimes(after 5-6 hours of uptime) it just stops working until the reboot, also I realized that frequency of this also affected by the kernel version
so it usually happened in the first hour of uptime in 4.15.0-45-generic and after 5-6 hours in 4.15.0-45-generic

> 
kkhamitov@kkhamitov-nix:~$ apt-cache policy xserver-xorg-input-synaptics 
xserver-xorg-input-synaptics:
  Installed: (none)
  Candidate: 1.8.2-1ubuntu3
  Version table:
     1.8.2-1ubuntu3 500
        500 [http://mirror.yandex.ru/ubuntu](http://mirror.yandex.ru/ubuntu) xenial/main amd64 Packages

xorg:
  Installed: 1:7.7+13ubuntu3.1
  Candidate: 1:7.7+13ubuntu3.1

Xorg log 
[https://pastebin.com/LkhzCDW3](https://pastebin.com/LkhzCDW3)



---

