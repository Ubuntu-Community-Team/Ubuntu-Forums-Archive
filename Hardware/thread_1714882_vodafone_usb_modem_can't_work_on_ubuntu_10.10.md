---
title: "vodafone usb modem can't work on ubuntu 10.10"
date: 2011-03-26
forum: Hardware
---

### Post by rachmat.hidayat on 2011-03-26
dear guys.. 

I need your help, 
I can't using my usb modem on ubuntu 10.10. 

I use vodafone usb modem, without detail information of what type or chipset used.
Here is what I can collect, when I plugged the usb modem to laptop.. 

result of dmesg.. 

---start---
[  956.873758] usb 1-1.1: new high speed USB device using ehci_hcd and address 5
[  956.974318] scsi5 : usb-storage 1-1.1:1.0
[  957.974336] scsi 5:0:0:0: CD-ROM            HSDPA    MMC Storage      2.31 PQ: 0 ANSI: 2
[  957.975167] scsi 5:0:0:1: Direct-Access     HSDPA    MMC Storage      2.31 PQ: 0 ANSI: 2
[  957.983404] sr1: scsi-1 drive
[  957.983762] sr 5:0:0:0: Attached scsi CD-ROM sr1
[  957.984435] sr 5:0:0:0: Attached scsi generic sg3 type 5
[  957.985652] sd 5:0:0:1: Attached scsi generic sg4 type 0
[  957.992792] sd 5:0:0:1: [sdc] Attached SCSI removable disk
[  958.720414] usb 1-1.1: USB disconnect, address 5
[  958.949682] usb 1-1.1: new high speed USB device using ehci_hcd and address 6
[  959.146804] scsi6 : usb-storage 1-1.1:1.3
---end---


and the result of lsusb command:

---start---
Bus 002 Device 003: ID 04f2:b1aa Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 05c6:0018 Qualcomm, Inc. 
Bus 001 Device 004: ID 03f0:231d Hewlett-Packard 
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
---end---

how can I troubleshoot the problem, so the usb modem can work properly.
may thanks, 
any kind of supported response will highly appreciated

---

### Post by nikhilbuwa on 2011-03-26
for using ur usb stick u should create a new connection "mobile broedband" with apn "www" (india) or whatever... then number(to dial) *99# & thats it just connect....
this worked for me earlier... but now have some prob.... try it.....
u can also use software to do this...
[https://forge.betavine.net/frs/?group_id=76](https://forge.betavine.net/frs/?group_id=76)
just download all 4 packages... & install in order....
hope that works...
the prob i have is here
[http://ubuntuforums.org/showthread.php?t=1714540](http://ubuntuforums.org/showthread.php?t=1714540)

---

### Post by nikhilbuwa on 2011-03-26
[U]u can also try "join air" dont have the link now... search for join air for linux
[/U][]("http://ubuntuforums.org/showthread.php?t=1714540")

---

