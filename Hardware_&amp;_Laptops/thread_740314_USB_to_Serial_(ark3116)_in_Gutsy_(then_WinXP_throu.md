---
title: "USB to Serial (ark3116?) in Gutsy (then WinXP through VMWare)"
date: 2008-03-30
forum: Hardware &amp; Laptops
---

### Post by callanbrown on 2008-03-30
Hey guys!

Ok so I've been scouring but haven't found a good answer.
I have a USB to serial cable that I know was working back in windows xp. lsusb shows the device as 6547:0232 which seems to be an ark3116 chipset.

Can someone tell me what steps I need to take to get this cable detected in Gutsy, then how to map that port to a device in VMWare, so I can install a driver there? 

thanks!

---

### Post by callanbrown on 2008-03-30
May have gotten this working.. can't test till I actually get back to the lab tomorrow.. but I did modprobe usbserial and modprobe ark3116. found /dev/ttyUSB0 and /dev/ttyS0 to be in existence. I installed a serial port in VMware and it said ttyS0 wasn't a serial port, but it accepted ttyUSB0. Hopefully that's all I need!

---

### Post by callanbrown on 2008-03-31
Hmm not working, the Parallax program says that there's no BASIC stamps found, meaning that it's not seeing the robot. Any ideas?

---

