---
title: "CF card and 9.04"
date: 2009-04-30
forum: Hardware
---

### Post by jborup on 2009-04-30
Hi community

I have a FujitsuSiemens computer with slots for different cards. I have a Sandisk CompactFlash card that I use in my camera. When I inserted this card into the card read'er with 8.10, I got presented with GUI, where I could select to run Fspot or open the disk.

After upgrading to 9.04, nothing happens when I insert the CF. 

I do a 'sudo tail -f /var/log/messages' nothing happens when I insert the card.

When I run lsusb, I get this:
maja@maja-desktop:~$ lsusb
Bus 001 Device 005: ID 0bf8:100f Fujitsu Siemens Computers 
Bus 001 Device 004: ID 07b8:e004 D-Link Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 04b3:3001 IBM Corp. 
Bus 003 Device 002: ID 04b3:3108 IBM Corp. 800dpi Optical Mouse w/ Scroll Point
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Same result with and without the SD. I can see that I have something called D-Link Mass Storage device.... ??? Got no clue what that is. I have only a keyboard and mouse connected to the usb.

Could someone give me a clue on how to get 9.04 to read my CF.

by the way, my card read'er has a green ligth, and when i insert the CF cart, a orange ligth goes on, and stays on as long the card is inserted. I cant remenber how it used to work with 8.10.

Regards Joern

---

### Post by celem on 2009-12-20
For whatever its worth, I couldn't see my CF card until I reformatted it "sudo mkfs -t vfat -n CF -v /dev/sdc1".

---

