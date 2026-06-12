---
title: "2 Issues with my Gateway W650A"
date: 2012-01-21
forum: Hardware
---

### Post by Rufio20 on 2012-01-21
Hello all!

I'm a relative noobie to Linux and I've run across a few issues with my 11.10 installation on a Gateway W650A. Please bear with me. :)

issue number 1: 
I managed to get the wireless card to work after following some instructions I found on an older thread
[http://ubuntuforums.org/showthread.php?t=575785](http://ubuntuforums.org/showthread.php?t=575785)

The problem I'm having is every time I restart the machine, the wireless card no longer works until I type the following commands in:
```
sudo ndiswrapper -m
sudo depmod -a
sudo modprobe ndiswrapper
```

Is there any way to make this permanent? 

Issue number 2: 
I'm a bit confused about the difference between open source video drivers and proprietary. Nothing pops up when I open up Additional Drivers, and I tried installing manually following the directions here
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
without any luck. Should I stick with open source? 
This is what I get when entering the LSPCI | grep VGA command:
```
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
```


Any help would be fantastic!

---

### Post by Rufio20 on 2012-01-22
Also, it seems any changes I make in the unity plugin on CCSM are not taking effect. Is this related to using the default video driver?

---

