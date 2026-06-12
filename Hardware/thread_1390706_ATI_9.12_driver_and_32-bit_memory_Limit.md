---
title: "ATI 9.12 driver and 32-bit memory Limit"
date: 2010-01-25
forum: Hardware
---

### Post by gotmonkey on 2010-01-25
I am running 9.04 Jaunty 32-bit and my system that has 6GB of memory and my system is only seeing 3GB. I know that this is a limitation of the kernel. I have read that installing the server kernel resolves this issue. My question is the ATI 9.12 compatible with the server kernel? 

Original Posting: 
[_**UbuntuGeek link**_]("http://www.ubuntugeek.com/how-to-use-more-than-3gb-ram-on-32-bit-ubuntu.html")


> You need to install the following packages and restart your PC

sudo apt-get install linux-restricted-modules-server

sudo apt-get install linux-headers-server

sudo apt-get install linux-image-server linux-server

That’s it after rebooting you should be able to see all the memory available in your system.

Any ideas or thoughts? thanks

---

### Post by cascade9 on 2010-01-25
Slightly old, but this tells you the various ways you can use 3GB+ with unbuntu-

[http://ubuntuforums.org/showthread.php?t=855511](http://ubuntuforums.org/showthread.php?t=855511)

Using the server kernel is the last of the 3 ways I'd go with. 64bit is easy these days, if you computer supports 64bit then I'd use it.

---

### Post by gotmonkey on 2010-01-26
I decided to take a risk, since this was a new install. Installed the server kernel. 

System booted fine and the ati driver was still working. 

The ATI control panel would not come up. 
Re-ran the ATI driver install, reboot, control panel now works. 

I have access to all 6GB of memory and my display is good.

---

