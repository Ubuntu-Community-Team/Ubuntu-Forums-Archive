---
title: "Huawei E220 HSDPA USB Modem issue after upgrade from 9.04 to 9.10"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by prishedko on 2009-10-30
Hi.

I've upgraded Ubuntu from 9.04 to 9.10 on Toshiba Satellite A200-23C laptop and after that I cannot establish connection with help of Huawei E220 HSDPA USB Modem. If I boot by using kernel 2.6.31-14-generic, it looks like OS persistently connects and disconnects the modem:

[B]...
Oct 30 21:59:35 bogdan-laptop kernel: [  109.062314] USB Serial support registered for GSM modem (1-port)
Oct 30 21:59:35 bogdan-laptop kernel: [  109.062417] option 7-1:1.0: GSM modem (1-port) converter detected
Oct 30 21:59:35 bogdan-laptop kernel: [  109.062573] usb 7-1: GSM modem (1-port) converter now attached to ttyUSB0
Oct 30 21:59:35 bogdan-laptop kernel: [  109.062598] option 7-1:1.1: GSM modem (1-port) converter detected
Oct 30 21:59:35 bogdan-laptop kernel: [  109.062709] usb 7-1: GSM modem (1-port) converter now attached to ttyUSB1
Oct 30 21:59:35 bogdan-laptop kernel: [  109.062749] usbcore: registered new interface driver option
Oct 30 21:59:35 bogdan-laptop kernel: [  109.062754] option: v0.7.2:USB Driver for GSM modems
Oct 30 22:00:01 bogdan-laptop kernel: [  134.819314] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Oct 30 22:00:01 bogdan-laptop kernel: [  134.819362] option 7-1:1.0: device disconnected
Oct 30 22:00:01 bogdan-laptop kernel: [  134.819520] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
Oct 30 22:00:01 bogdan-laptop kernel: [  134.819561] option 7-1:1.1: device disconnected
...
Oct 30 22:00:01 bogdan-laptop kernel: [  134.929061] usb 7-1: reset full speed USB device using uhci_hcd and address 3
Oct 30 22:00:01 bogdan-laptop kernel: [  135.076336] option 7-1:1.1: GSM modem (1-port) converter detected
Oct 30 22:00:01 bogdan-laptop kernel: [  135.076497] usb 7-1: GSM modem (1-port) converter now attached to ttyUSB0
Oct 30 22:00:01 bogdan-laptop kernel: [  135.080956] option 7-1:1.0: GSM modem (1-port) converter detected
Oct 30 22:00:01 bogdan-laptop kernel: [  135.081179] usb 7-1: GSM modem (1-port) converter now attached to ttyUSB1
Oct 30 22:00:01 bogdan-laptop kernel: [  135.113139] scsi 11:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
Oct 30 22:00:01 bogdan-laptop kernel: [  135.136107] sr1: scsi-1 drive
Oct 30 22:00:01 bogdan-laptop kernel: [  135.136513] sr 11:0:0:0: Attached scsi generic sg3 type 5
Oct 30 22:00:13 bogdan-laptop kernel: [  146.651140] sr: Sense Key : No Sense [current] 
Oct 30 22:00:13 bogdan-laptop kernel: [  146.651150] sr: Add. Sense: No additional sense information
Oct 30 22:00:13 bogdan-laptop kernel: [  146.949164] sr: Sense Key : No Sense [current] 
Oct 30 22:00:13 bogdan-laptop kernel: [  146.949174] sr: Add. Sense: No additional sense information
Oct 30 22:00:13 bogdan-laptop kernel: [  147.151230] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
Oct 30 22:00:13 bogdan-laptop kernel: [  147.151258] option 7-1:1.0: device disconnected
Oct 30 22:00:13 bogdan-laptop kernel: [  147.151344] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Oct 30 22:00:13 bogdan-laptop kernel: [  147.151368] option 7-1:1.1: device disconnected
...
[/B]
(full messages file in attachment).

If I use kernel 2.6.28-16-generic, I cannot log in in gnome session because of touchpad doesn't work, so I don't know modem works in kernel 2.6.28-16-generic or doesn't.

Could somebody help me please to solve this issue?

---

### Post by jouni on 2009-11-06
This is probably [Bug #446146]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146").

---

### Post by prishedko on 2009-11-06
Thanks a lot!

---

### Post by esmailgad on 2010-02-12
If you still having problem to connect your E220, you can use my "how to- http://ubuntuforums.org/showthread.php?t=1404649". I had the same problem. TILL ME IF YOU WANT HELP
Bye

---

### Post by GeorgeVita on 2010-02-12
... consider also a possible firmware update as at:
[http://ubuntuforums.org/showpost.php?p=8499795&postcount=9](http://ubuntuforums.org/showpost.php?p=8499795&postcount=9)

AND a kernel update of Ubuntu 9.10 (using wifi or ethernet) due to bug# [446146]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146")

Although wvdial connects you most times, E220 can be used easier via network manager.

Regards,
George

---

