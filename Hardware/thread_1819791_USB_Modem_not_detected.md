---
title: "USB Modem not detected"
date: 2011-08-06
forum: Hardware
---

### Post by damnthisbloodycomputer on 2011-08-06
I have recently made the switch from Windows to Ubuntu. WOW!! Why has it taken me so long to discover the amazing world of Linux?
I am having trouble installing my Huawei E160e USB modem. Ubuntu is detecting it as a mass storage device instead of a modem. I have tried configuring the Mobile Broadband settings manually through Edit Connections ->  but have had no luck.
I have also tried using usb_modeswitch but this does not seem to help either. I have spent hours trawlling through pages of posts on various websites with no success, so any suggestions would be VERY gratefully received!!

---

### Post by JC Cheloven on 2011-08-06
Hi, in my experience, if it doesn't work out of the box, it can be a pita to make it to work. Sometimes simply unmounting the detected mass storage makes the system to "see" the device. If not:
- You can start [here]("http://ubuntuforums.org/showthread.php?t=843973") for a basic procedure. 
- You can try some additions from [here]("http://www.fk21.co.uk/cgi-bin/fk21.cgi?sub=tmobile")
- Additional link: [this]("http://www.fk21.co.uk/tmobilelinux/wvdial.txt").

That's what I used some time ago for a Huawei E220 anyway. Hope it helps.

---

### Post by damnthisbloodycomputer on 2011-08-07
Many thanks for the links. I'll give it a go and let you know how I get on

---

### Post by cavalier911 on 2011-08-10
Identify the USB Modem:
```
lsusb
```
If the device id is 12d1:140c
Look here:
[http://www.niiranen.fi/Tech-Blog/solvedubuntu1010andhuaweie160e12d1140c](http://www.niiranen.fi/Tech-Blog/solvedubuntu1010andhuaweie160e12d1140c)
[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?p=3307&sid=0b14471182781e0ecd4affbfa8537a40](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?p=3307&sid=0b14471182781e0ecd4affbfa8537a40)

---

