---
title: "US Robotics USR5422"
date: 2011-09-02
forum: Hardware
---

### Post by Antonjo on 2011-09-02
I have an USB Wi-Fi dongle US Robotics USR5422.

I followed the procedure described here:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

The adapter works for a few seconds, then the system completely freezes and I have to hard reset.

I tried to compile myself the ndiswrapper-1.56.tar.gz but I get the error:

Unknown field 'ioctl' specified in initializer


I tried also to install/compile ndiswrapper dpkg. 
  
I wire-connected the laptop and updated the system.

No luck in any cases.

Note that I ran a live Puppy Linux on an USB stick and the adapter was recognised automatically out of the box.
 
Can you help?


I have an AMD Athlon XP m 2600 laptop, 512 Mega RAM DDR, 
with Lubuntu 11

Thanks in advance
Antonio

---

### Post by Antonjo on 2011-09-06
The solution can be found here:

[http://ubuntuforums.org/showthread.php?t=1838434](http://ubuntuforums.org/showthread.php?t=1838434)

You may find interesting an alternative solution at the end of the thread:

[http://ubuntuforums.org/showpost.php?p=11225340&postcount=26](http://ubuntuforums.org/showpost.php?p=11225340&postcount=26)
 
Antonio

---

