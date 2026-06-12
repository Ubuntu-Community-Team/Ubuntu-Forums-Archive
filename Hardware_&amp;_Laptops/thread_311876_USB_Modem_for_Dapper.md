---
title: "USB Modem for Dapper"
date: 2006-12-03
forum: Hardware &amp; Laptops
---

### Post by IMELucky on 2006-12-03
Hey everybody!
It's almost christmas time and I would like to ask my parents for a USB modem for my laptop that will work with Dapper.

Could somebody point to a USB modem that is known to work with dapper?

I also need to point out that my parents are really computer illiterate and are scared of shopping online, so I need specific make and models, and where it can be bought. Otherwise they might get confused and get me something else, and I really do need this modem!

Thanks for the help!

---

### Post by jdong on 2006-12-03
I don't recommend USB modems for Linux.... they typically are software modems in general with poor Linux support.

I still prefer good fashioned serial external modems if you're looking for absolute compatibility.... and the last time I looked at the dial-up world closely (6 months or so ago), 3COM and US Robotics still had the most reliable modems though they are a bit pricey and not as awesome as they were before the two companies merged.

---

### Post by IMELucky on 2006-12-04
Thanks for the reply, but my laptop doesn't have a serial port.

How well do PCMIA modems work?

---

### Post by jdong on 2006-12-04
PCMCIA modems can stand a better chance of working because some of them are indeed hardware-based. Do research carefully though :)

(P.S. there are USB-to-serial converters for less than 10 bucks on online retailers :) )

---

### Post by A. J. Rimmer on 2006-12-04
I agree with the usb-to-serial suggestion.  I have an IoGear usb-to-serial adapter that works well with my HP laptop.  I got lucky and found a used serial modem for $15 at a local shop.  I set the modem address in System / Applications / Networking to /dev/ttyUSB0 and it worked on the first try.

---

### Post by IMELucky on 2006-12-04
Sweet! I'll give it a shot. Thanks everybody!

---

### Post by jdong on 2006-12-05
Also, I would not completely rule out the possibility of using a winmodem/softmodem if you fully do your research and show that it does work under Linux.

I have a hardware USR5692 external serial modem, which is arguably the best modem that money can buy. I also have a Lucent/Agere WinModem (known by codename Mars, 1648C, used by a lot of OEM's) which I use under both Windows and Linux perfectly fine. My laptop has a Conexant HDA codec softmodem and Linuxant produces paid drivers for Linux. I've installed their trial drivers and they work just fine.

Remember that now with V.92 and V.44 compression, hardware modems limited at 115.2K cannot accomodate the burst speeds that your modem can potentially deliver, while software and DSP modems do not have this issue.

And no, lots of the WinModem drivers aren't purely open source, but your hardware modems don't have open source flash ROM either ;-)

---

### Post by IMELucky on 2006-12-05
I've tried jumping through the hoops trying to configure winmodems under Linux before, and in my experience it has been an absolute nightmare. But since Linux is becoming more popular I was beginning to wonder if modem venders are actually supporting Linux or not. This is kind of what prompted my question in the first place.

Normally dail-up isn't even an issue because I have broadband internet when I'm at college. However, when I'm home I have to use Windows to go on the internet because the winmodem in my laptop doesn't seem to be supported. 

Does Ubuntu maintain a hardware compatibility database so that I can check what make/models of modems are known to work and which ones aren't?

---

### Post by jdong on 2006-12-05
Ubuntu doesn't have that accurate a hardware compatibility database, no, unfortunately.


What kind of winmodem is in your laptop?

---

### Post by IMELucky on 2006-12-05
output of lspci
0000:00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)

If this isn't enough info then I'll need help determing the modem type

---

### Post by jdong on 2006-12-05
> **IMELucky said:**
> output of lspci
0000:00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)

If this isn't enough info then I'll need help determing the modem type

It seems like a codec modem of some sort. Do you have links  to the Windows drivers for the device?

---

### Post by IMELucky on 2006-12-05
Ok
Windows Identifies it as a:
Agere Systems AC'97 Modem and it operates on COM4

I found this link
[http://www.versiontracker.com/dyn/moreinfo/win/65434](http://www.versiontracker.com/dyn/moreinfo/win/65434)

which when I clicked on download driver it took me to microsoft's update website

If it will help, the windows driver uses the following files:
C:\WINDOWS\agrsmdel.exe
C:\WINDOWS\AGRSMMSG.exe
C:\WINDOWS\System32\DRIVERS\AGRSM.sys <---I'm guessing this is the driver file?
C:\WINDOWS\System32\drivers\Modem.sys

I could provide any one of these files if you need them.

Thanks

---

### Post by jdong on 2006-12-05
That's an Agere AMR softmodem which is not supported under Linux.

---

### Post by IMELucky on 2006-12-05
Thanks for the info

---

