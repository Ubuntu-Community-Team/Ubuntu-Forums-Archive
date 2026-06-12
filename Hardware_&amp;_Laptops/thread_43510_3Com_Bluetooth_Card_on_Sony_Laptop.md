---
title: "3Com Bluetooth Card on Sony Laptop"
date: 2005-06-22
forum: Hardware &amp; Laptops
---

### Post by jonesam31 on 2005-06-22
Good afternoon,
I am writing to enquire about an issue I'm having, it is as follows. I have a Sony Vaio Laptop (VGN-B1XP) with Ubuntu Linux installed (2.6.10-5-386) and a 3Com Bluetooth Card (3CRWB6096), I have installed all of the bluez utilities and unzipped the firmware file from 3Com (BT3CPCC.bin), when i insert the card i get the following error is dmesg: 
 
bt3c_open: Firmware request failed 
bt3c_interrupt: Call if irq 3 for unknown device
 
And in syslog:
 
kernel: cs: pcmcia_socket: unable to supply power
cardmgr[6912]: socket 0: 3Com Bluetooth PC Card
cardmgr[6912]: executing: 'modprobe bt3c_cs'
kernel: bt3c_open: Firmware request failed 
kernel: bt3c_interrupt: Call if irq 3 for unknown device
cardmgr[6912]: get dev info on socket 0 failed: Resource temporarily unavailable
 
It seems to me that the issue is that bt3c_cs cannot find the firmware file, although i have tried everywhere noted on the net. I have also tried changing the reference in bt3c_cs from BT3CPCC.bin to /T3CPCC.bin and dropping that file in the system root.
 
I think its looking (for the firmare) somewhere specific to Ubuntu but i can't find where.

If you have any ideas they would be greatly appreciated.
Many thanks,
 
Andy Jones

---

### Post by nolifer on 2006-02-19
[http://ubuntuforums.org/showthread.php?p=749901]("http://ubuntuforums.org/showthread.php?p=749901")

I have the same problem. Anyone?

---

