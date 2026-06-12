---
title: "Printing problem&quot; ubuntu 10.04 &amp; Canon LBP-1120"
date: 2010-06-12
forum: Hardware
---

### Post by Pavluha88 on 2010-06-12
Can smb help to solve following problem please:
 
I managed to install drivers for Canon LASER SHOT LBP-1120 after quite some time of reading google (surching different ubuntu forums). Now there is a problem - after I started computer and send some document to print it does not getting printed but just stuck in print queue as "Process" and never get printed. But when I manually restart cups with 
```
sudo /etc/init.d/cups restart
```
 
and turn off and turn on printer and send document for printing again it starting to print. After future reboot of PC the situation repeating again.
 
While I was installing printer drivers I set up this rule for printer turn on and turn off:
 
```

sudo -i
 
echo 'KERNEL=="lp*", SUBSYSTEMS=="usb", ACTION=="add", SYSFS{idVendor}=="04a9", RUN+="/bin/bash /etc/init.d/ccpd start"' >> /etc/udev/rules.d/85-canon-capt.rules
 
echo 'KERNEL=="lp*", SUBSYSTEMS=="usb", ACTION=="remove", RUN+="/bin/bash /etc/init.d/ccpd stop"' >> /etc/udev/rules.d/85-canon-capt.rules

```
 
How better to handle this problem in the way so printer service normally works after computer get loaded?
 
The printer is on USB.
**Model:** Canon LASER SHOT LBP-1120. 
I was installing original drivers from Canon web-site, version 1.80. But while I was making it installed I installed something else (many things per different instructions from internet :) ) and do not remind what exactly.
 
**OS:** Ubuntu 10.04 LTS
 
**Core**: 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux
 
**lsusb**:
[Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 005: ID 04a9:262b Canon, Inc. LaserShot LBP-1120 Printer
Bus 007 Device 003: ID 09da:000a A4 Tech Co., Ltd Port Mouse
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 
**dmesg | tail**:
[ 189.001228] usblp0: nonzero read bulk status received: -84
[ 189.128100] usb 7-1: USB disconnect, address 4
[ 189.135911] __ratelimit: 12 callbacks suppressed
[ 189.135918] ccpd[1660]: segfault at 0 ip 08052b44 sp bfe670f0 error 4 in ccpd[8048000+c000]
[ 189.136186] usblp0: removed
[ 192.840107] usb 7-1: new full speed USB device using uhci_hcd and address 5
[ 193.019362] usb 7-1: configuration #1 chosen from 1 choice
[ 193.026328] usblp0: USB Bidirectional printer dev 5 if 0 alt 0 proto 2 vid 0x04A9 pid 0x262B
[ 194.273932] usb 7-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[ 215.716477] soffice.bin[1534]: segfault at 86d05e9 ip 086d05e9 sp b3c8e1a0 error 4 in libavahi-common.so.3.5.1[88a6000+a000]

---

### Post by Pavluha88 on 2010-06-14
Now I added that Canon drivers daemon starting at bootup ```
/etc/init.d/ccpd start
```

For right now printer starting to print when after computer bootup to shutdown and start it again. Does smb knows how to fix it?

---

### Post by Pavluha88 on 2010-06-14
Handled!
Added to autostart at system bootup:

> /etc/init.d/ccpd restart

---

### Post by Pavluha88 on 2010-06-16
There is new bug if smb can help to solve:
If there is in printer only one sheet of paper and I send to print a task which require more then one **** so the printer print first page, I turn it around and put back for print second page BUT printer is printing first one again and it is repeating until I put more then one sheets of paper inside. Looks like printer send "error" command when a task was not printed in full (due to lack of paper sheets) and starting to print from the beginning.

Did smb had the same?

---

