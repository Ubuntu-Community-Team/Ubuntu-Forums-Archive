---
title: "Thinkpad T61 Modem"
date: 2009-07-18
forum: Hardware
---

### Post by diskmaster23 on 2009-07-18
I have been having trouble trying to get my internal modem to work on my Thinkpad T61. I used the scanModem program and followed the instructions but it still does not work.
I am using Ubuntu 9.04 Jaunty.

---

### Post by curley_sue on 2009-08-17
check out (or see below):
[https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant)
(which is based on:)
[http://ubuntuforums.org/showthread.php?t=1015673&page=2](http://ubuntuforums.org/showthread.php?t=1015673&page=2)

used to work for me on T61 sub-model: 7664-1FG
with 64bit ubuntu

haven't tried that in a while (but used to send/receive faxes)
if it does not work for you, I may try again...

u will have to download the drivers from (make sure to download the relevant one, depending on whether you are running 32 or 64 bit ubuntu)
(copying from the original post):
- download the newest driver from linuxant (source version!)
[http://www.linuxant.com/drivers/hsf/full/downloads.php](http://www.linuxant.com/drivers/hsf/full/downloads.php)

- download from (the link I found was dead so I put the one I believe is the relevant one)
[http://linux.dell.com/files/ubuntu/hardy/modem-drivers/hsf/](http://linux.dell.com/files/ubuntu/hardy/modem-drivers/hsf/)

- unpack both

- replace the /modules/imported directory in the linuxant-version with that from dell

- sudo make install
- sudo hsfconfig


I believe to also have installed:
[http://www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.20.3/alsa-driver-linuxant_1.0.20.3_all.deb.zip](http://www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.20.3/alsa-driver-linuxant_1.0.20.3_all.deb.zip)

hope that helps (let me know...)

---

