---
title: "Bamboo Wacomin 9.10 not working -.-"
date: 2009-11-12
forum: Hardware
---

### Post by Lemontree on 2009-11-12
Aloha!

Hi everyone, i bought an grafiktablett, the Bamboo MTE-450A, and now wanted to getting it working on ubuntu 9.10, i plugged in the tablet, but still no reaction from the system.

if i type in terminal : "lsusb"
```
Bus 001 Device 004: ID 056a:0065 Wacom Co., Ltd 
```

So i guess the system see in someway that a wacom tablett is pluged in. But i got no idea why, it still not working in anyway.

I got the drivers installed from the synaptic packeges. 

I searched around in different forums, but most instructions made for earlier ubuntu versions.

thx so far, for your advice
Lemontree

---

### Post by Favux on 2009-11-12
Hi Lemontree,

Enter in a terminal:
```
lsmod
```
and see if you see "wacom".  Or you could try:
```
lsmod | grep [Ww]acom
```
Anyway if wacom isn't there edit the 'modules' file in "/etc/" and add "wacom" (without the quotes) at the end of the file.
```
gksudo gedit /etc/modules
```
And then reboot.

---

