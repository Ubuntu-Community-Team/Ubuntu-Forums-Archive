---
title: "HP printer error"
date: 2011-02-08
forum: Hardware
---

### Post by amin2084 on 2011-02-08
im using HP laserjet 1020 series, when im trying to print word document, the message popup said, "the printer is not on9". I've check the printer cable and restart its again but the same problem and message still popup. i ended up to switch to Windows and try to print from windows and the printer is working. so thats means the printer is still on9 but cannot print on Ubuntu OS. Anyone can help me to solve these problem. Thanks in advance.

Im Beginner

---

### Post by gabhla on 2011-02-09
Try this :

1. install (if you haven't already) hplip and hplip-gui

   sudo apt-get install hplip hplip-gui

2. issue the following, and following the instructions

   sudo hp-setup -i

---

### Post by amin2084 on 2011-02-10
ok. thanks. i've already install hplip and hplip-gui. and then on the second step
2) sudo hp-setup -i but the erroe message appear at terminal. for info, the printer is connected with usb. I dont know what happen. any idea?

this appear at the terminal


--------------------------------
| SELECT CONNECTION (I/O) TYPE |
--------------------------------

  Num       Connection  Description                                               
            Type                                                                  
  --------  ----------  ----------------------------------------------------------
  0*        usb         Universal Serial Bus (USB)                                
  1         net         Network/Ethernet/Wireless (direct connection or JetDirect)
  2         par         Parallel Port (LPT:)                                      

Enter number 0...2 for connection type (q=quit, enter=usb*) ? 0

Using connection type: usb

error: No device selected/specified or that supports this functionality.

---

### Post by amin2084 on 2011-02-10
ok. problem found. previously i didnt isntall hplip and hplip-gui and the printer is still working. and then im installing hplip-gui as suggested by someone on my previous post but then the printer not working. n then i try to issue the 

sudo hp-setup -i but unfortunately my printer is offline. i forgot to switch it on. thanks ghabla. my printer working now. :)

---

