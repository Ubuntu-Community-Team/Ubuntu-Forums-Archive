---
title: "128 gb ssd in usb 3.0 case not seen"
date: 2015-05-25
forum: Hardware
---

### Post by Joe_Linux on 2015-05-25
I have a 128 gb ssd (Sandisk) in an external usb 3.0 case not seen by Ubuntu 12.04. 

Specifically in g-parted any help would be appreciated.

---

### Post by Vladlenin5000 on 2015-05-25
Not seen if connected on boot or not even seen if reconnected later?

---

### Post by Joe_Linux on 2015-05-25
No  Not seen if connected on boot or connected later

---

### Post by Joe_Linux on 2015-05-25
I tried it under under 14.04 ssd still not seen

---

### Post by Vladlenin5000 on 2015-05-25
With the drive connected, what results give *lsusb*? 
If the device shows up then, hardware wise, it's being recognized and should work. Somehow the OS isn't mounting it and there are many different reasons for such behaviour.
If not, the problem is somewhere else.

In a nutshell, this is the first troubleshooting step. Everything else depends on determining the aforementioned condition.

---

### Post by Joe_Linux on 2015-05-25
the result of lsusb 
fred@fred-System-Product-Name:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0e8f:0022 GreenAsia Inc. 
Bus 003 Device 003: ID 046d:c05a Logitech, Inc. Optical Mouse M90
Bus 005 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
fred@fred-System-Product-Name:~$

---

### Post by Vladlenin5000 on 2015-05-25
I see no external drive there so you have a problem.

I suppose you already tested that drive in some other computer successfully. If not, now it's a good time to do it, just in case.
Assuming the drive is in working condition elsewhere then the problem is either your USB ports or an incompatibility. Not all USB3.0 device work is older USBs. They should but some simply refuse to work in USB2.0.

---

### Post by kryten35 on 2015-05-25
Also check your usb3 cable.I got a new external usb3 drive last month and the supplied cable was completely dead.
Worked after i tried another another one.

---

### Post by shantiq on 2015-05-26
Hi Joe went through a very similar process of recent times
maybe read this section of the following thread starting [ here]("http://ubuntuforums.org/showthread.php?t=2265824&p=13230789#post13230789")   and carrying on

I use an external 128GB SSD in a [caddie]("http://www.akasa.com.tw/update.php?tpl=product/product.detail.tpl&no=181&type=Enclosures&type_sub=2.5%20Enclosure&model=AK-TL2SEB-BK") but use usb3 **and sata** to link it to computer .    that way it is picked up.  the caddie only cost about £20 and because of sata the speeds are great


It may be a solution for you here too ...   have a read    


PS   as you will see i knew nothing but was guided mostly by Sudodus;   my computer is ancient [2005]   but now with this it purrs like a young puma on crack ...   well worth the effort/investment


shan

---

