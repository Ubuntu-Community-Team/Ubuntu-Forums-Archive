---
title: "Bluetooth mouse connects but does not move pointer."
date: 2014-05-10
forum: Hardware
---

### Post by zhangweiwu on 2014-05-10
Ubuntu 14.04. Bluetooth add new device wizard finished without any error. Bluetooth applet shows Bluetooth enabled. The applet shows that the mouse is connected too, if user (me) click it once. It can auto-reconnect this way on reboot. Whenever it is 'connected', power applet can show the batter remains for the mouse.

The problem: cursor doesn't move. In fact, if I boot into Windows 8.0 on the same host, the cursor moves. The same mouse works fine on Windows XP too.It doesn't have on/off switch.

dmesg:
```
[  129.914221] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[  129.914256] Bluetooth: HIDP socket layer initialized
[  129.916595] hid-generic 0005:0A5C:0001.0005: unknown main item tag 0x0
[  129.953134] input: Bluetooth Mouse as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/bluetooth/hci0/hci0:21/input14
[  129.954447] hid-generic 0005:0A5C:0001.0005: input,hidraw4: BLUETOOTH HID v0.1e Keyboard [Bluetooth Mouse] on 74:f0:6d:81:bd:72

```

The device mentioned in dmesg does not exist as a file node in that path (perhaps wasn't supposed to):
```

$ ls /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/bluetooth/hci0/hci0:21/input14
ls: no se puede acceder a /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/bluetooth/hci0/hci0:21/input14: No existe el archivo o el directorio

```

XINPUT has:

```
$ xinput
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; eGalax Inc. USB TouchController         	id=9	[slave  pointer  (2)]
&#9116;   &#8627; eGalax Inc. USB TouchController Pen     	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Trackball                  	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Bluetooth Mouse                         	id=17	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Heng Yu Technology Poker II             	id=12	[slave  keyboard (3)]
    &#8627; Heng Yu Technology Poker II             	id=13	[slave  keyboard (3)]
    &#8627; USB 2.0 Camera                          	id=14	[slave  keyboard (3)]
    &#8627; Asus Laptop extra buttons               	id=15	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=16	[slave  keyboard (3)]

```

Attempt to enable device id=17 has no effect. I am afraid it is always enabled:
```

$ xinput --enable 17

```

It seems the mouse device does not send any data to the host when the cursor not moving. The following CODE demonstrate that:
1. computer boots without mouse3 device (mouse not 'oiled' by Windows)
2. user click bluetooth mouse and mouse3 device come to exist, that means mouse3 is the USB mouse
3. but it doesn't generate any data when moving, compare to a real mouse mouse2

```

$ ls
by-id    event1   event12  event4  event7  js0     mouse1
by-path  event10  event2   event5  event8  mice    mouse2
event0   event11  event3   event6  event9  mouse0
$ ls 
by-id    event1   event12  event3  event6  event9  mouse0  mouse3
by-path  event10  event13  event4  event7  js0     mouse1
event0   event11  event2   event5  event8  mice    mouse2
$ sudo -i
# od < /dev/input/mouse3 
^C
# od < /dev/input/mouse2
0000000 177430 034000 177777 174070 034377 177364 171070 034375
0000020 177766 171070 034375 176765 173070 034373 176367 174470
0000040 034374 175367 175070 034373 175775 176470 034375 177375
0000060 177470 034377 177777 177470 014377 000377 176470 014377
0000100 000771 172430 014001 000764 172030 014002 000766 173030
0000120 014001 001371 175030 014001 000775 177030 014001 000377
^C

```

The most singular thing that happened is: in one occassion, I boot into Windows 8 and use the mouse, when I reboot back, the cursor go on moving for a few minutes and mute. It seems, using it in Windows 'oils' the mouse. But I couldn't repeatly reproduce this. I am very certain about this. The cursor doesn't move even right after the first time add-new-bluetooth device wizard quit successfully, the single one time it worked, is after Windows 8 oiled it.

I'm clueless, any hint? (a physical mouse is attached to test pointer as comparison and it works)

---

### Post by zhangweiwu on 2014-05-11
Do you think it is a bug of the bluetooth driver? My devices are:

$ lspci
00:00.0 Host bridge: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 04)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
01:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
02:00.0 Multimedia controller: Broadcom Corporation BCM70015 Video Decoder [Crystal HD]

---

### Post by zhangweiwu on 2014-05-12
Seeing no response, submitted this as bug. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1318639](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1318639)

---

