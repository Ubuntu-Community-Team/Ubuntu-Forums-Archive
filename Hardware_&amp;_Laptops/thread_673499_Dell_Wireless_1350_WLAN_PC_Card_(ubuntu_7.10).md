---
title: "Dell Wireless 1350 WLAN PC Card (ubuntu 7.10)"
date: 2008-01-20
forum: Hardware &amp; Laptops
---

### Post by gypsumwolf on 2008-01-20
Wireless card is Dell Wireless 1350 WLAN PC Card.

O/S is Ubuntu 7.10 (Fresh and default install)

I tried NDISwrapper. I used same driver that works in windows XP.

It said "driver installed" or something very similar than:

```
default@TheShire:~$ cd Desktop
default@TheShire:~/Desktop$ ls
bcmwl5.inf  bcmwl5.sys
default@TheShire:~/Desktop$ sudo iwconfig
[sudo] password for default:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

default@TheShire:~/Desktop$ sudo iwlist
Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 
default@TheShire:~/Desktop$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

```

---

### Post by pyan on 2008-01-22
Hello,
Try this step:
1: download "bcm43xx-firmware_1.3-1ubuntu2_all.deb" from [http://ubuntu.cafuego.net/pool/feisty-cafuego/bcm43xx/bcm43xx-firmware_1.3-1ubuntu2_all.deb](http://ubuntu.cafuego.net/pool/feisty-cafuego/bcm43xx/bcm43xx-firmware_1.3-1ubuntu2_all.deb)
2: install that package
3: I waited 10 - 20 second ( according to speed of machine )
4: I typed at terminal "sudo modprobe bcm43xx"
n my wireless device work in excellent condition.
hope this help.....

---

### Post by az on 2008-01-22
In 7.10, you are supposed to be able to install the firmware for the BCM kernel drive using the restricted-drivers-manager in System-Administration.  Did you try this before ndiswrapper?

---

