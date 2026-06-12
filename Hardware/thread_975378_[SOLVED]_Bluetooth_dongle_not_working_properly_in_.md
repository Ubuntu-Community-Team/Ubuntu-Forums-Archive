---
title: "[SOLVED] Bluetooth dongle not working properly in Intrepid"
date: 2008-11-08
forum: Hardware
---

### Post by yurukov on 2008-11-08
I have a Motorola Bluetooth dongle PC850. It works with Widcomm drives under windows. When I hook it up under Intrepid, it is recognized and the icon pops up, however it does not discover any of my devices. I also have a fake dongle, that under windows does not work at all, but yet in ubuntu at least discovers the devices. That's why I think this is a drivers problem. 

I use stereo headset Motorola HT820 and a Prophet-style Pocket PC running on Windows. Both devices worked with the Motorola dongle under windows. 

Can anyone help me fix it. Using the headset with my laptop was my primary concern when I decided to move to Linux.

---

### Post by yurukov on 2008-11-20
I tried to install the windows drivers using ndiswrapper and it said it could find the hardware, but I can't use it in any way. None of the standard bluetooth tools work. It seems that the system does not recognize the dongle as such wen using the windows drivers.

Then I uninstalled the drivers and now the dongle is not found at all. Before at least the bluetooth wizard popped up, even though it couldn't find anything.

---

### Post by Yezinki on 2008-11-20
ubuntu@ubuntu-laptop:~$ lsusb
Bus 005 Device 006: ID 0ac8:c002 Z-Star Microelectronics Corp. Visual Communication Camera VGP-VCC1
Bus 005 Device 004: ID 054c:031d Sony Corp. 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 054c:024b Sony Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0609:031d SMK Manufacturing, Inc. eHome Infrared Receiver
**Bus 001 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)**
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ubuntu@ubuntu-laptop:~$ 


BT dongle works with no issues!

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-20
It detects my N 93 my Dell XPS with out a problem.

Good luck.

Regards,

Yezinki.

---

### Post by yurukov on 2008-11-20
lsusb shows:
...
Bus 003 Device 007: ID 22b8:0850 Motorola PCS Bluetooth Device
..

The bluetooth manager in Intrepid still does not recognize a device. hcitool also says that there is no bluetooth device connected. I reinstalled all bluetooth* and bluez* programs and uninstalled the windows driver and the ndiswrapper and still nothing.

---

### Post by Yezinki on 2008-11-20
I had no issues just plugged in & started functioning........never had the need of any drivers.........WIDDCOM etc.

I got mine from Circuity City for 20 bucks........

---

### Post by yurukov on 2008-11-20
When I plugged the other bt dongle, the wizard showed up. lsusb showed "Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)" like in your case. However when I tried to discover other bt devices, it crashed and now it has the same problem as the other one - shows on lsusb, but hcitool scan doesn't find it. I wonder what did I screw up.

---

### Post by Yezinki on 2008-11-20
Wizard never came up for me???

---

### Post by yurukov on 2008-11-20
But when you started it, it was able to find some devices. The same goes for "hcitool scan". On my computer the latter says that there is no bluetooth device hooked up, although lsusb says otherwise.

---

### Post by Yezinki on 2008-11-20
It found 2 devices in a sec.......Nokia N93 & Dell XPS!

---

### Post by Yezinki on 2008-11-20
Are you typing the correct pw??

---

### Post by Yezinki on 2008-11-20
Don't ever use substandard hardware!!

---

### Post by yurukov on 2008-11-20
Further responses in [this thread]("http://ubuntuforums.org/showthread.php?p=6219885&posted=1#post6219885").

---

### Post by Cope57 on 2008-11-20
This thread should  be merged with [http://ubuntuforums.org/showthread.php?t=964139](http://ubuntuforums.org/showthread.php?t=964139)
The other topic almost identical to this one.

---

### Post by yurukov on 2008-11-20
That's why I cut the discussion in the previous post.

---

