---
title: "TigerJet phone for ubuntu: setting permissions for hid services"
date: 2007-11-19
forum: Hardware &amp; Laptops
---

### Post by pcreed on 2007-11-19
I am having trouble using a TigerJet usb phone adapter with Ubuntu 7.10.  I downloaded TigerJet's linux driver from [http://www.cuphone.com/software/download/tjinit_skype-1.6-0.i586.rpm]("http://www.cuphone.com/software/download/tjinit_skype-1.6-0.i586.rpm") and installed it using Alien. However, I need to set access permissions for my HID services and the instructions given at [http://www.cuphone.com/help/linux.htm#skype]("http://www.cuphone.com/help/linux.htm#skype") does not include ubuntu. It would seem that I need to change the permissions on a file called hiddev0 but this does not exist on my computer. Is there some mistake in my configuration that I need to fix to create this file?

Relevant outputs follow:

pcreed@mardyke:~$ tjinit_skype 
pcreed@mardyke:~$ X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Please grant permissions on your HID devices

pcreed@mardyke:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 06e6:831c Tiger Jet Network, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

pcreed@mardyke:~$ ls -l /sys/bus/usb/drivers/
total 0
drwxr-xr-x 2 root root 0 2007-11-19 21:12 hub
drwxr-xr-x 2 root root 0 2007-11-19 22:22 snd-usb-audio
drwxr-xr-x 2 root root 0 2007-11-19 22:13 usb
drwxr-xr-x 2 root root 0 2007-11-19 22:13 usbfs

Thanks

---

