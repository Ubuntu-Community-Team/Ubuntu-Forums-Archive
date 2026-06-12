---
title: "HP laserjet 3050 on DAPPER 64 - not recognized by usb"
date: 2006-08-08
forum: Hardware &amp; Laptops
---

### Post by xiko on 2006-08-08
Hello, I have an AMD 64 with a GYGABYTE motherboard with nforce4.

Everything works fine, sound, network, usb mouse.

But my printer is not recognized in the usb, all the guides related to install the thing is supposed to have the printer recognized in the usb port.

Ideas of what can I do ?

---

### Post by xiko on 2006-08-08
UPDATE
The dmesg command gave me this about the usb:

[   27.061513] usb 2-1: new high speed USB device using ehci_hcd and address 2
[   27.173365] usb 2-1: device descriptor read/64, error -71
[   27.389083] usb 2-1: device descriptor read/64, error -71
[   27.500939] Probing IDE interface ide1...
[   27.604801] usb 2-1: new high speed USB device using ehci_hcd and address 3
[   27.716656] usb 2-1: device descriptor read/64, error -71
[   27.932373] usb 2-1: device descriptor read/64, error -71


I've tried multiple alternatives with this problem on google but all solutions didn't work out.

---

### Post by xiko on 2006-09-04
I found the error.

I was using an 1.1 usb cable to connect my printer. Even in the 1.1 port it would not work.

I've got a 2.0 cable and now it is working fine.

---

### Post by Buffalo Soldier on 2006-09-13
Is it the HP LaserJet 3050 All-in-One? I was thinking of purchasing that all-in-one printer. How is it working for you? Is all the print, fax, copy & scan function working correctly?

[http://h10010.www1.hp.com/wwpc/my/en/sm/WF05a/1090037-1090149-1090429-1090429-1794093-12245328.html](http://h10010.www1.hp.com/wwpc/my/en/sm/WF05a/1090037-1090149-1090429-1090429-1794093-12245328.html)

---

### Post by Chemroydal Tissue on 2007-04-12
Bump, because I'm looking to buy one of these, too. Anyone own one of these?

---

### Post by gary441 on 2007-04-17
I have a HP Laserjet 3050 on Edgy and so far I can't get it installed.
I run thru the "New Printer" and it is detected and the wizard finishes. But the printer is not listed.

lsusb
Bus 001 Device 003: ID 03f0:3217 Hewlett-Packard

dmesg
[17181915.600000] usb 1-2: new high speed USB device using ehci_hcd and address 3
[17181915.732000] usb 1-2: configuration #1 chosen from 1 choice
[17181916.236000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 0 alt 1 proto 2 vid 0x03F0 pid 0x3217
[17181916.236000] usbcore: registered new driver usblp
[17181916.236000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver


No errors are far as I can see, it doesn't list the printer and I can't print. Might have to break out the old HP laserjest  4L

Gary

---

### Post by Chemroydal Tissue on 2007-04-25
Hm. Looks like I'll to find another solution. Thanks.

---

