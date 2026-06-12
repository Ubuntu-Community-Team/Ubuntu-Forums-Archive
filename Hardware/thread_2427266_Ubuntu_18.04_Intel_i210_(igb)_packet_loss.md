---
title: "Ubuntu 18.04 Intel i210 (igb) packet loss"
date: 2019-09-20
forum: Hardware
---

### Post by avshutko on 2019-09-20
I have an issue with some Intel Atom based singleboard pc. It have two gigabit i210 interfaces. There is a problem with speed and link. I installed ubuntu 18.04 (kernel 4.15.0-47) and got network speed 150-300 Kb/s and unstable link (10 cable plugs leads to 7 link up).


But. **After rmmod igb/modprobe igb speed became 90-95 Mbps / 700-800 Mbps **so it looks like this is not a hardware problem.


ethtool -S enp1s0 shows many crc errors when speed low and 0 crc errors after rmmod igb/modprobe igb.


I tried:


1. New kernel 4.18 - speed became 80-100kb (rmmod igb/modprobe igb still restore normal speed)
2. Set speed and duplex on both line ends to 100/full - not helped
3. Debian 8 image from board manufacturer - speed 60-70 Mbps after boot and very strong link unstability (10 cable plugs and 1 link up)
4. Some manupulation with BIOS settings - not helped at all
5. Tried cable with 2 pairs (green and orange) - link became stable (100 mbit) but speed issue not gone.
6. Download, compile and install Intel igb driver 5.3.5.36 (from Intel site) - no visible changes.

So I need an advise how to diagnose and solve this issue...

---

### Post by avshutko on 2019-09-26
It was hardware problem - flat cable between mainboard and RJ45 board. Flat cable (300mm length) was replaced by twisted pairs and problem gone...

---

