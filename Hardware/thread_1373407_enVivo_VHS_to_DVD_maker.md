---
title: "enVivo VHS to DVD maker"
date: 2010-01-05
forum: Hardware
---

### Post by PaulNL on 2010-01-05
Hello a pall of me had a enVivi VHS to DVD maker, question is can i get it to work with Ubuntu 9.04 ??

I have also asked the question on a Dutch forum but for now it looks it is stuck.

When i use lsusb i get:
 device is connected:
Bus 001 Device 009: ID 048d:9009 Integrated Technology Express, Inc. 
Bus 001 Device 003: ID 04b4:6830 Cypress Semiconductor Corp. CY7C68300A EZ-USB AT2 USB 2.0 to ATA/ATAPI
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 093a:2510 Pixart Imaging, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Device not connected:
Bus 001 Device 003: ID 04b4:6830 Cypress Semiconductor Corp. CY7C68300A EZ-USB AT2 USB 2.0 to ATA/ATAPI
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 093a:2510 Pixart Imaging, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

When i connect it and look in the system-log i get
Jan  5 17:00:23 laptoppaul kernel: [ 5162.264094] usb 1-1: new high speed USB device using ehci_hcd and address 7
Jan  5 17:00:24 laptoppaul kernel: [ 5162.411909] usb 1-1: configuration #1 chosen from 1 choice

IDoes anyone know a way to use it in Ubuntu 9.04 ???

Thanks for now
Paul

---

### Post by Bubbel on 2011-01-04
Well, same here. Cannot get even a proper device listing with lsusb :(
Running 10.10, by the way.
Site: [http://www.teknihall.be]("http://www.teknihall.be")

---

### Post by gdkoning on 2011-01-24
I installed Oracle VM Virtual Box under Ubuntu, including Oracle Virtual Box Extensions. Then I installed Windows XP in the Virtual Box. Works fine, including Networking, etc. In this Virtual Machine I activated USB devices in Settings. Then I asked for a Filter from the device. The device was recognized as AFA Technologies Inc. ITE Video Capture Device (0200). Sofar so fine.

However the next problem was to use it. The program I tried was Power Director from Cyberlink. This requires more pixels in the window then my monitor can provide because Ubuntu keeps some space for the Menu at top. 

Maybe someone has a solution for this?;)

---

### Post by gdkoning on 2011-01-26
In the meantime I learned that Host+F under Oracle VM Virtualbox does the trick: you get a full screen for Windows, so I could use  the Cyberlink Power Director software. And the enVivo DVD maker works.......

Success:o

---

