---
title: "Looking for a cell phone/smartphone for my Ubuntu 7.10..."
date: 2007-11-11
forum: Hardware &amp; Laptops
---

### Post by IgnatiusReilly on 2007-11-11
I have recently installed Ubuntu 7.10 on my Dell laptop having only minor problems.
I am really satisfied, but for my printer and my old Canon scanner, that do not work under Linux.
Thus, I decided to spend some time looking for the full hardware compatibility BEFORE the purchase rather than spending hours searching in forums for a solution AFTER the purchase..

I have to buy a cell phone / smartphone and I want to know if there is any that is fully supported on Ubuntu, or at least with an eye to the Linux world.

The point is that I'd like not only to be able to transfer files, but rather to use all (or almost all) the features available on Windows (sync contacts, UMTS, etc.).

Do you know any?

---

### Post by scorp123 on 2007-11-11
Look at the "Sharp Zaurus" line or the Nokia N800 ... they come with Linux installed and should be easy to use I imagine. Anything based on "Windows Mobile" requires ActiveSync, and that one is a proprietary protocol. There are however a few models that work well with Linux ... check the compatibility list here: [http://www.synce.org](http://www.synce.org)

As for UMTS and using your mobile phone as modem: That one is easy. If you connect your phone via USB cable to your computer chances are that you get a **/dev/ttyACM0** device (check with "dmesg" after plugging the USB cable into your computer) and that one works like an ordinary modem. Here is e.g. my **/etc/wvdial.conf** for my GSM provider Swisscom. My phone is a **Sharp 770SH**:
```
[Dialer Swisscom]
Modem = /dev/ttyACM0
Baud = 460800
Dial Command = ATD
Init1 = ATZ 
Init2 = ATE1
Init3 = ATE0V1&D2&C1S0=0+IFC=2,2
ISDN = 0 
Modem Type = USB Modem
Phone = *99***1#
Username = ''
Password = ''
Stupid Mode = yes
Init5 = AT+CGDCONT=1,"IP","gprs.swisscom.ch","",0,0
``` The config for your provider may look different. I found all the infos I needed on my provider's web site. So now when I want to use my phone as UMTS modem I just need to launch this command: ```
sudo wvdial Swisscom
``` ... and I am connected.

---

### Post by IgnatiusReilly on 2007-11-12
Thanks a lot. I will certainly give a look at that phone.

Bye

---

### Post by scorp123 on 2007-11-12
> **IgnatiusReilly said:**
> Thanks a lot. I will certainly give a look at that phone.  You might also consider those various USB "mobile broadband" modems most operators offer these days. Most of those modems should work well. The **Huawei E220** (easily recognisable due to its white color and eliptic shape) does work pretty well; same goes for the **Novatel Ovation** USB sticks (I have the **"Novatel Ovation MC950D"** and it works tip top!). Look at the thread here:
[http://ubuntuforums.org/showpost.php?p=3749057&postcount=2](http://ubuntuforums.org/showpost.php?p=3749057&postcount=2)

---

