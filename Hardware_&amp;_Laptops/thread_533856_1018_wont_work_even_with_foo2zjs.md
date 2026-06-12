---
title: "1018 wont work even with foo2zjs"
date: 2007-08-24
forum: Hardware &amp; Laptops
---

### Post by jefisme03 on 2007-08-24
ubuntu feisty fawn wll not even detect my printer

---

### Post by w4ett on 2007-08-24
You will want to review this from Launchpad -Questions:

[https://answers.launchpad.net/ubuntu/+question/6695](https://answers.launchpad.net/ubuntu/+question/6695)

---

### Post by jefisme03 on 2007-08-24
ok that wont help as it dosent even detect it as a connected ie ubuntu cant see it

---

### Post by w4ett on 2007-08-24
What is the output of :

```
lsusb
```

Paste the results of the command

---

### Post by jefisme03 on 2007-08-24
john@john-desktop:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 001 Device 003: ID 046d:c51a Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  
john@john-desktop:~$

---

### Post by jefisme03 on 2007-08-24
ok so apparently is not getting picked up even on the usb port any more help?

---

### Post by w4ett on 2007-08-24
Try the printer in a different usb socket.......also try a reboot.  Might be a bad socket/plug or (gulp) printer problem.  Have you tried to connect the printer to a different computer?

---

### Post by jefisme03 on 2007-08-25
tried all those things even got it to print on my grandpas windows comp changed sockets checked both cords but still its not picking it up

---

### Post by w4ett on 2007-08-25
OK....give us the output of:
```
lspci
```

Then...just for giggles...try running the Live CD and then run the command:

```
lsusb
```

Trying to see is what USB chipset you have, then  to check what the default drivers do for the printer/usb  connectivity.  Not trying to run you in circles..just trying to troubleshoot.  :)  And further,  to verify,  you did run the HPLIP Toolbox?

---

### Post by jefisme03 on 2007-08-25
john@john-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:08.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:09.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:09.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:09.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:0a.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0a.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0c.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0d.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0d.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0d.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:0e.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:10.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:12.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:16.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:17.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0193 (rev a2)
02:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
04:00.0 Mass storage controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)

---

### Post by jefisme03 on 2007-08-25
ubuntu@ubuntu:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c51a Logitech, Inc. 
Bus 001 Device 002: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 001 Device 001: ID 0000:0000  
ubuntu@ubuntu:~$

---

### Post by jefisme03 on 2007-08-25
Bus 002 Device 003: ID 046d:c51a Logitech, Inc. 
Bus 002 Device 002: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by mshafahi on 2007-11-05
I have the same problem some one help!
It works with 7.04 but not with 7.10

---

