---
title: "Prior usb devices stop working yet new one work"
date: 2019-08-25
forum: Hardware
---

### Post by sam-flory on 2019-08-25
I rebooted my system today and found every usb device connected to it had stopped working.  Strangely plugging in a different keyboard and mouse works fine.  

Non working:
```
Aug 25 19:04:25 tower kernel: [  460.225605] usb 1-3: USB disconnect, device number 11
Aug 25 19:04:27 tower kernel: [  461.975324] usb 1-3: new high-speed USB device number 12 using xhci_hcd
Aug 25 19:04:27 tower kernel: [  462.141834] usb 1-3: New USB device found, idVendor=148f, idProduct=3070, bcdDevice= 1.01
Aug 25 19:04:27 tower kernel: [  462.141840] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Aug 25 19:04:27 tower kernel: [  462.141843] usb 1-3: Product: 802.11 n WLAN
Aug 25 19:04:27 tower kernel: [  462.141846] usb 1-3: Manufacturer: Ralink
Aug 25 19:04:27 tower kernel: [  462.141849] usb 1-3: SerialNumber: 1.0
Aug 25 19:04:27 tower mtp-probe: checking bus 1, device 12: "/sys/devices/pci0000:00/0000:00:14.0/usb1/1-3"
Aug 25 19:04:27 tower mtp-probe: bus: 1, device: 12 was not an MTP device
Aug 25 19:04:27 tower mtp-probe: checking bus 1, device 12: "/sys/devices/pci0000:00/0000:00:14.0/usb1/1-3"
Aug 25 19:04:27 tower mtp-probe: bus: 1, device: 12 was not an MTP device
Aug 25 19:04:32 tower kernel: [  467.175835] usb 1-5.3: USB disconnect, device number 7
Aug 25 19:04:35 tower kernel: [  470.011325] usb 1-5.3: new low-speed USB device number 13 using xhci_hcd
Aug 25 19:04:35 tower kernel: [  470.169576] usb 1-5.3: New USB device found, idVendor=056e, idProduct=00fe, bcdDevice= 1.20
Aug 25 19:04:35 tower kernel: [  470.169581] usb 1-5.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Aug 25 19:04:35 tower kernel: [  470.169585] usb 1-5.3: Product: ELECOM TrackBall Mouse
Aug 25 19:04:35 tower kernel: [  470.169587] usb 1-5.3: Manufacturer: ELECOM
Aug 25 19:04:35 tower mtp-probe: checking bus 1, device 13: "/sys/devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5.3"
Aug 25 19:04:35 tower mtp-probe: bus: 1, device: 13 was not an MTP device
Aug 25 19:04:35 tower mtp-probe: checking bus 1, device 13: "/sys/devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5.3"
Aug 25 19:04:35 tower mtp-probe: bus: 1, device: 13 was not an MTP device
Aug 25 19:04:37 tower kernel: [  472.295818] usb 1-5.1: USB disconnect, device number 5
Aug 25 19:04:40 tower kernel: [  474.831304] usb 1-5.1: new full-speed USB device number 14 using xhci_hcd
Aug 25 19:04:40 tower kernel: [  474.947631] usb 1-5.1: New USB device found, idVendor=046d, idProduct=c52b, bcdDevice=12.03
Aug 25 19:04:40 tower kernel: [  474.947634] usb 1-5.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Aug 25 19:04:40 tower kernel: [  474.947635] usb 1-5.1: Product: USB Receiver
Aug 25 19:04:40 tower kernel: [  474.947637] usb 1-5.1: Manufacturer: Logitech
Aug 25 19:04:40 tower mtp-probe: checking bus 1, device 14: "/sys/devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5.1"
Aug 25 19:04:40 tower mtp-probe: bus: 1, device: 14 was not an MTP device
Aug 25 19:04:40 tower mtp-probe: checking bus 1, device 14: "/sys/devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5.1"
Aug 25 19:04:40 tower mtp-probe: bus: 1, device: 14 was not an MTP device

Working:
Aug 25 19:09:26 tower kernel: [  761.299152] usb 1-5.2: new full-speed USB device number 21 using xhci_hcd
Aug 25 19:09:27 tower kernel: [  761.414478] usb 1-5.2: New USB device found, idVendor=062a, idProduct=4102, bcdDevice=81.13
Aug 25 19:09:27 tower kernel: [  761.414483] usb 1-5.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Aug 25 19:09:27 tower kernel: [  761.414486] usb 1-5.2: Product: 2.4G Wireless Mouse
Aug 25 19:09:27 tower kernel: [  761.414489] usb 1-5.2: Manufacturer: MOSART Semi.
Aug 25 19:09:27 tower kernel: [  761.420321] input: MOSART Semi. 2.4G Wireless Mouse as /devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5.2/1-5.2:1.0/0003:062A:4102.0013/input/input20
Aug 25 19:09:27 tower kernel: [  761.479523] input: MOSART Semi. 2.4G Wireless Mouse as /devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5.2/1-5.2:1.0/0003:062A:4102.0013/input/input21
Aug 25 19:09:27 tower kernel: [  761.481521] hid-generic 0003:062A:4102.0013: input,hiddev0,hidraw1: USB HID v1.10 Mouse [MOSART Semi. 2.4G Wireless Mouse] on usb-0000:00:14.0-5.2/input0
Aug 25 19:09:27 tower mtp-probe: checking bus 1, device 21: "/sys/devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5.2"
Aug 25 19:09:27 tower mtp-probe: bus: 1, device: 21 was not an MTP device
Aug 25 19:09:27 tower /usr/lib/gdm3/gdm-x-session[3935]: (II) config/udev: Adding input device MOSART Semi. 2.4G Wireless Mouse (/dev/input/mouse0)
Aug 25 19:09:27 tower /usr/lib/gdm3/gdm-x-session[3935]: (II) No input driver specified, ignoring this device.
Aug 25 19:09:27 tower /usr/lib/gdm3/gdm-x-session[3935]: (II) This device may have been added with another device file.
Aug 25 19:09:27 tower /usr/lib/gdm3/gdm-x-session[2026]: (II) config/udev: Adding input device MOSART Semi. 2.4G Wireless Mouse (/dev/input/mouse0)
Aug 25 19:09:27 tower /usr/lib/gdm3/gdm-x-session[2026]: (II) No input driver specified, ignoring this device.
Aug 25 19:09:27 tower /usr/lib/gdm3/gdm-x-session[2026]: (II) This device may have been added with another device file.
Aug 25 19:09:27 tower /usr/lib/gdm3/gdm-x-session[3935]: (II) config/udev: Adding input device MOSART Semi. 2.4G Wireless Mouse (/dev/input/event4)
Aug 25 19:09:27 tower /usr/lib/gdm3/gdm-x-session[3935]: (**) MOSART Semi. 2.4G Wireless Mouse: Applying InputClass "evdev pointer catchall"
Aug 25 19:09:27 tower /usr/lib/gdm3/gdm-x-session[3935]: (**) MOSART Semi. 2.4G Wireless Mouse: Applying InputClass "libinput pointer catchall"
Aug 25 19:09:27 tower /usr/lib/gdm3/gdm-x-session[3935]: (II) Using input driver 'libinput' for 'MOSART Semi. 2.4G Wireless Mouse'
Aug 25 19:09:27 tower /usr/lib/gdm3/gdm-x-session[2026]: (II) config/udev: Adding input device MOSART Semi. 2.4G Wireless Mouse (/dev/input/event4)
Aug 25 19:09:27 tower /usr/lib/gdm3/gdm-x-session[2026]: (**) MOSART Semi. 2.4G Wireless Mouse: Applying InputClass "evdev pointer catchall"
Aug 25 19:09:27 tower /usr/lib/gdm3/gdm-x-session[2026]: (**) MOSART Semi. 2.4G Wireless Mouse: Applying InputClass "libinput pointer catchall"
Aug 25 19:09:27 tower /usr/lib/gdm3/gdm-x-session[2026]: (II) Using input driver 'libinput' for 'MOSART Semi. 2.4G Wireless Mouse'
Aug 25 19:09:27 tower /usr/lib/gdm3/gdm-x-session[3935]: (II) systemd-logind: got fd for /dev/input/event4 13:68 fd 47 paused 0
Aug 25 19:09:27 tower /usr/lib/gdm3/gdm-x-session[3935]: (**) MOSART Semi. 2.4G Wireless Mouse: always reports core events
Aug 25 19:09:27 tower /usr/lib/gdm3/gdm-x-session[3935]: (**) Option "Device" "/dev/input/event4"
Aug 25 19:09:27 tower /usr/lib/gdm3/gdm-x-session[3935]: (**) Option "_source" "server/udev"
Aug 25 19:09:27 tower /usr/lib/gdm3/gdm-x-session[2026]: (II) systemd-logind: got fd for /dev/input/event4 13:68 fd 25 paused 1
Aug 25 19:09:27 tower /usr/lib/gdm3/gdm-x-session[2026]: (II) systemd-logind: releasing fd for 13:68
Aug 25 19:09:27 tower /usr/lib/gdm3/gdm-x-session[3935]: (II) event4  - MOSART Semi. 2.4G Wireless Mouse: is tagged by udev as: Mouse
Aug 25 19:09:27 tower /usr/lib/gdm3/gdm-x-session[3935]: (II) event4  - MOSART Semi. 2.4G Wireless Mouse: device is a pointer
Aug 25 19:09:27 tower /usr/lib/gdm3/gdm-x-session[3935]: (II) event4  - MOSART Semi. 2.4G Wireless Mouse: device removed
Aug 25 19:09:27 tower /usr/lib/gdm3/gdm-x-session[3935]: (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5.2/1-5.2:1.0/0003:062A:4102.0013/input/input20/event4"
Aug 25 19:09:27 tower /usr/lib/gdm3/gdm-x-session[3935]: (II) XINPUT: Adding extended input device "MOSART Semi. 2.4G Wireless Mouse" (type: MOUSE, id 10)
Aug 25 19:09:27 tower /usr/lib/gdm3/gdm-x-session[3935]: (**) Option "AccelerationScheme" "none"
Aug 25 19:09:27 tower /usr/lib/gdm3/gdm-x-session[3935]: (**) MOSART Semi. 2.4G Wireless Mouse: (accel) selected scheme none/0
Aug 25 19:09:27 tower /usr/lib/gdm3/gdm-x-session[3935]: (**) MOSART Semi. 2.4G Wireless Mouse: (accel) acceleration factor: 2.000
Aug 25 19:09:27 tower /usr/lib/gdm3/gdm-x-session[3935]: (**) MOSART Semi. 2.4G Wireless Mouse: (accel) acceleration threshold: 4
Aug 25 19:09:27 tower /usr/lib/gdm3/gdm-x-session[3935]: (II) event4  - MOSART Semi. 2.4G Wireless Mouse: is tagged by udev as: Mouse
Aug 25 19:09:27 tower /usr/lib/gdm3/gdm-x-session[3935]: (II) event4  - MOSART Semi. 2.4G Wireless Mouse: device is a pointer
Aug 25 19:09:27 tower /usr/lib/gdm3/gdm-x-session[3935]: (II) config/udev: Adding input device MOSART Semi. 2.4G Wireless Mouse (/dev/input/event5)
Aug 25 19:09:27 tower /usr/lib/gdm3/gdm-x-session[3935]: (II) No input driver specified, ignoring this device.
Aug 25 19:09:27 tower /usr/lib/gdm3/gdm-x-session[3935]: (II) This device may have been added with another device file.
Aug 25 19:09:27 tower /usr/lib/gdm3/gdm-x-session[2026]: (II) config/udev: Adding input device MOSART Semi. 2.4G Wireless Mouse (/dev/input/event5)
Aug 25 19:09:27 tower /usr/lib/gdm3/gdm-x-session[2026]: (II) No input driver specified, ignoring this device.
Aug 25 19:09:27 tower /usr/lib/gdm3/gdm-x-session[2026]: (II) This device may have been added with another device file.
Aug 25 19:09:27 tower mtp-probe: checking bus 1, device 21: "/sys/devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5.2"
Aug 25 19:09:27 tower mtp-probe: bus: 1, device: 21 was not an MTP device

devices:

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh=10
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=05.00
S:  Manufacturer=Linux 5.0.0-25-generic xhci-hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#=0x0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#= 15 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0bc2 ProdID=2100 Rev=00.00
S:  Manufacturer=Seagate
S:  Product=FreeAgent
S:  SerialNumber=2GE3CT36
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#=0x0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=01 Lev=01 Prnt=01 Port=03 Cnt=02 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0d8c ProdID=0014 Rev=01.00
S:  Manufacturer=C-Media Electronics Inc.
S:  Product=VTIN VNPA081AB
C:  #Ifs= 4 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#=0x0 Alt= 0 #EPs= 0 Cls=01(audio) Sub=01 Prot=00 Driver=(none)
I:  If#=0x1 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=(none)
I:  If#=0x2 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=(none)
I:  If#=0x3 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid

T:  Bus=01 Lev=01 Prnt=01 Port=04 Cnt=03 Dev#=  4 Spd=480 MxCh= 4
D:  Ver= 2.10 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=2109 ProdID=2813 Rev=90.11
S:  Manufacturer=VIA Labs, Inc.
S:  Product=USB2.0 Hub
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#=0x0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=02 Prnt=04 Port=00 Cnt=01 Dev#= 14 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c52b Rev=12.03
S:  Manufacturer=Logitech
S:  Product=USB Receiver
C:  #Ifs= 3 Cfg#= 1 Atr=a0 MxPwr=98mA
I:  If#=0x0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
I:  If#=0x1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
I:  If#=0x2 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid

T:  Bus=01 Lev=02 Prnt=04 Port=01 Cnt=02 Dev#= 21 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=062a ProdID=4102 Rev=81.13
S:  Manufacturer=MOSART Semi.
S:  Product=2.4G Wireless Mouse
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#=0x0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid

T:  Bus=01 Lev=02 Prnt=04 Port=02 Cnt=03 Dev#= 13 Spd=1.5 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=056e ProdID=00fe Rev=01.20
S:  Manufacturer=ELECOM
S:  Product=ELECOM TrackBall Mouse
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#=0x0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid

T:  Bus=01 Lev=02 Prnt=04 Port=03 Cnt=04 Dev#= 18 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=413c ProdID=2113 Rev=01.08
S:  Product=Dell KB216 Wired Keyboard
C:  #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#=0x0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
I:  If#=0x1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 4
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=05.00
S:  Manufacturer=Linux 5.0.0-25-generic xhci-hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#=0x0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
```

---

### Post by Autodave on 2019-08-26
I will admit that I have no idea what that means that you posted.  But, my gut feeling is that you may have too mane items plugged in and that your 5v line is too low.  Are any of these plugged into powered USB hubs?

I would start by disconnecting every one of them and then trying one at a time.

---

### Post by sam-flory on 2019-08-26
It turns out a week or two ago I cleaned out a bunch of orphaned kernel debs for space.  And some how I removed linux-modules-extras....  It was just shear luck that my old devices all had drivers in the base modules deb.  Here I was thinking that I'd found some weird udev misconfig.

---

### Post by wildmanne39 on 2019-08-26
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

