---
title: "Jolicloud eGalax Touchscreen Swap Axes"
date: 2011-01-28
forum: Hardware
---

### Post by redcodefinal on 2011-01-28
Hi,
I just installed an eGalax TouchScreen into an Acer Apsire One and everything works except the axes need to be swapped. I've tried everything, the TKCal program won't pick up the TouchScreen, Their GUI tool tells me it can't find it. Yet somehow it works >_>. Also, xinput doesn't see to work. 

lsusb
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 064e:d101 Suyin Corp. Acer CrystalEye Webcam
Bus 001 Device 003: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Command I tried to run but, says no device found
```
xinput set-prop --type=int --format=8 "Ltd eGalax TouchScreen" "Evdev Axes Swap" 1
```

Any help appreciated!

---

### Post by craigsmith86 on 2012-10-25
Hello,

I know this post is ancient, but I have worked out where you've been going wrong.

My touchscreen on Joli 1.2 was behaving the same as yours and I fixed it with the following steps.

1 find out what id your touchscreen it via # "xinput list"
(most likely to be 10 or 11.

2 list the properties of your screen with xinput list-props <yourid>

3 invert the axis with the following command:

xinput set-prop <yourid> --type=int --format=8 "Evdev Axis Inversion" 0, 1

Hope this helps

---

