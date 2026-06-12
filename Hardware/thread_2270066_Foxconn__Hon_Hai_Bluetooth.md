---
title: "Foxconn / Hon Hai Bluetooth"
date: 2015-03-20
forum: Hardware
---

### Post by adam133 on 2015-03-20
Hey all,

I've done a cursory search over these forums and didn't find any information about this bluetooth adapter. Forgive me if I've missed something!

I have an Acer Aspire v5-122p. The laptop came stock with windows 8, and the same day I bought it I converted it to ubuntu. Everything works flawlessly except for bluetooth. The bluetooth settings allow me to turn bluetooth on and off as well as make the device discoverable. However, it cannot detect nearby bluetooth devices and bluetooth devices cannot seem to find it.

I did a quick check through dmesg

```
fayk@morningstar:~$ dmesg | grep -i bluetooth[   30.661185] Bluetooth: Core ver 2.17
[   30.661272] Bluetooth: HCI device and connection manager initialized
[   30.661293] Bluetooth: HCI socket layer initialized
[   30.661300] Bluetooth: L2CAP socket layer initialized
[   30.661310] Bluetooth: SCO socket layer initialized
[   32.892688] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   32.892698] Bluetooth: BNEP filters: protocol multicast
[   32.892719] Bluetooth: BNEP socket layer initialized
[   32.908687] Bluetooth: RFCOMM TTY layer initialized
[   32.908719] Bluetooth: RFCOMM socket layer initialized
[   32.908734] Bluetooth: RFCOMM ver 1.11
```

which doesn't show the bluetooth driver loading. Looking at lsusb, I see the device is recognized (it's the Foxconn / Hon Hai):

```
fayk@morningstar:~$ lsusb
Bus 002 Device 002: ID 1bcf:2c17 Sunplus Innovation Technology Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 04f3:009d Elan Microelectronics Corp. 
Bus 004 Device 002: ID 0489:e05f Foxconn / Hon Hai 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

usb-devices shows the bluetooth driver
```
T:  Bus=04 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0489 ProdID=e05f Rev=00.01
C:  #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
```

I found the following on linuxquestions, but I'm not sure it applies to my device, and compiling linux kernel modules is a bit over my head: [http://www.linuxquestions.org/questions/slackware-14/%5Bsolved%5D-bluetooth-adapter-not-working-0489-e027-foxconn-hon-hai-4175430169/](http://www.linuxquestions.org/questions/slackware-14/%5Bsolved%5D-bluetooth-adapter-not-working-0489-e027-foxconn-hon-hai-4175430169/)

Any suggestions for getting bluetooth working on this laptop would be greatly appreciated!

---

### Post by dino99 on 2015-03-20
maybe try:

sudo hciconfig hci1 reset
and
sudo restart bluetooth

and be sure to use the latest bios version

---

### Post by jeremy31 on 2015-03-21
> **adam133 said:**
> Hey all,

I've done a cursory search over these forums and didn't find any information about this bluetooth adapter. Forgive me if I've missed something!

I have an Acer Aspire v5-122p. The laptop came stock with windows 8, and the same day I bought it I converted it to ubuntu. Everything works flawlessly except for bluetooth. The bluetooth settings allow me to turn bluetooth on and off as well as make the device discoverable. However, it cannot detect nearby bluetooth devices and bluetooth devices cannot seem to find it.

I did a quick check through dmesg

```
fayk@morningstar:~$ dmesg | grep -i bluetooth[   30.661185] Bluetooth: Core ver 2.17
[   30.661272] Bluetooth: HCI device and connection manager initialized
[   30.661293] Bluetooth: HCI socket layer initialized
[   30.661300] Bluetooth: L2CAP socket layer initialized
[   30.661310] Bluetooth: SCO socket layer initialized
[   32.892688] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   32.892698] Bluetooth: BNEP filters: protocol multicast
[   32.892719] Bluetooth: BNEP socket layer initialized
[   32.908687] Bluetooth: RFCOMM TTY layer initialized
[   32.908719] Bluetooth: RFCOMM socket layer initialized
[   32.908734] Bluetooth: RFCOMM ver 1.11
```

which doesn't show the bluetooth driver loading. Looking at lsusb, I see the device is recognized (it's the Foxconn / Hon Hai):

```
fayk@morningstar:~$ lsusb
Bus 002 Device 002: ID 1bcf:2c17 Sunplus Innovation Technology Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 04f3:009d Elan Microelectronics Corp. 
Bus 004 Device 002: ID 0489:e05f Foxconn / Hon Hai 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

usb-devices shows the bluetooth driver
```
T:  Bus=04 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0489 ProdID=e05f Rev=00.01
C:  #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
```

I found the following on linuxquestions, but I'm not sure it applies to my device, and compiling linux kernel modules is a bit over my head: [http://www.linuxquestions.org/questions/slackware-14/%5Bsolved%5D-bluetooth-adapter-not-working-0489-e027-foxconn-hon-hai-4175430169/](http://www.linuxquestions.org/questions/slackware-14/%5Bsolved%5D-bluetooth-adapter-not-working-0489-e027-foxconn-hon-hai-4175430169/)

Any suggestions for getting bluetooth working on this laptop would be greatly appreciated!

Your bluetooth device is an Atheros that needs firmware provided by liinux-firmware package but there is a problem with xhci-hcd that prevents ath3k from loading the firmware at times.  See if you can install kernel 3.16.0-32 as the xhci_hcd issue is fixed in that kernel

If nothing else post ```
uname -a
``` and I can modify the source code so that your bluetooth will work

---

