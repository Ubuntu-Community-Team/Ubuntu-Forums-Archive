---
title: "Wireless network card"
date: 2007-03-15
forum: Hardware &amp; Laptops
---

### Post by scottie924 on 2007-03-15
I have an HP laptop and I have Ubuntu 6.10 and Kubuntu 6.10 installed.  I am unable to get the wireless driver installed.  At one point I got it to where I could see the wireless network but it would not connect.  Now I can't see it and the button on my laptop to turn the wireless card on and off does not work and is always off.  I'm new to linux and was wondering if someone would be able to help me get the wireless working.  I do have a wired network that works on the laptop.

---

### Post by scrooge_74 on 2007-03-17
Hope any of these helps, which card you have?

Maybe you will need to use ndiswrapper if there are no drivers for linux

[http://www.ubuntuforums.org/showthread.php?t=185174](http://www.ubuntuforums.org/showthread.php?t=185174)
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)
[http://ubuntuforums.org/showthread.php?t=282034](http://ubuntuforums.org/showthread.php?t=282034)

---

### Post by scottie924 on 2007-03-19
I have tried the first two links but they do not work.  I can not see the network card in Ubuntu.  Any other ideas? or anyone want to help step me through it either on here or using AIM or something like that?

---

### Post by scrooge_74 on 2007-03-20
My laptop has a similar on off switch but it is irrelevan since I installed Linux.  If you manage to saw the network maybe you should check if you had security on.

try sudo ifup eth1 (or what your system says is your card).

Post the brand and model of your card so others can give you more help.

I have been lucky that all three laptops I have use in the past two months the wireless cards have been detected from the begining.

---

