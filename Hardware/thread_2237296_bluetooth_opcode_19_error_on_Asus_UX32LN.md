---
title: "bluetooth opcode 19 error on Asus UX32LN"
date: 2014-07-31
forum: Hardware
---

### Post by akos.maroy on 2014-07-31
Hi,

I'm trying to get Bluetooth work on an Asus UX32LN laptop. this page: [https://help.ubuntu.com/community/AsusZenbook#Bluetooth](https://help.ubuntu.com/community/AsusZenbook#Bluetooth)  says that it should work out of the box. but, when I turn bluetooth on in preferences, it stays on for a while, the BT icon is not displayed in the top bar, then it turns off. in syslog, this is what I get:

```
Aug  1 05:46:58 UX kernel: [245695.133629] usb 1-4: new full-speed USB device number 11 using xhci_hcd
Aug  1 05:46:58 UX kernel: [245695.151214] usb 1-4: string descriptor 0 malformed (err = -61), defaulting to 0x0409
Aug  1 05:46:58 UX kernel: [245695.153530] usb 1-4: New USB device found, idVendor=13d3, idProduct=3393
Aug  1 05:46:58 UX kernel: [245695.153542] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Aug  1 05:46:58 UX kernel: [245695.190905] usb 1-4: USB disconnect, device number 11
Aug  1 05:46:59 UX kernel: [245695.461859] usb 1-4: new full-speed USB device number 12 using xhci_hcd
Aug  1 05:46:59 UX kernel: [245695.479452] usb 1-4: string descriptor 0 malformed (err = -61), defaulting to 0x0409
Aug  1 05:46:59 UX kernel: [245695.481312] usb 1-4: New USB device found, idVendor=13d3, idProduct=3393
Aug  1 05:46:59 UX kernel: [245695.481318] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Aug  1 05:46:59 UX bluetoothd[790]: Unknown command complete for opcode 19
Aug  1 05:46:59 UX bluetoothd[790]: Endpoint registered: sender=:1.69 path=/MediaEndpoint/HFPAG
Aug  1 05:46:59 UX bluetoothd[790]: Endpoint registered: sender=:1.69 path=/MediaEndpoint/HFPHS
Aug  1 05:46:59 UX bluetoothd[790]: Endpoint registered: sender=:1.69 path=/MediaEndpoint/A2DPSource
Aug  1 05:46:59 UX bluetoothd[790]: Endpoint registered: sender=:1.69 path=/MediaEndpoint/A2DPSink
Aug  1 05:46:59 UX bluetoothd[790]: Unregister path: /org/bluez/790/hci0
Aug  1 05:46:59 UX bluetoothd[790]: Endpoint unregistered: sender=:1.69 path=/MediaEndpoint/A2DPSink
Aug  1 05:46:59 UX bluetoothd[790]: Endpoint unregistered: sender=:1.69 path=/MediaEndpoint/A2DPSource
Aug  1 05:46:59 UX bluetoothd[790]: Endpoint unregistered: sender=:1.69 path=/MediaEndpoint/HFPAG
Aug  1 05:46:59 UX bluetoothd[790]: Endpoint unregistered: sender=:1.69 path=/MediaEndpoint/HFPHS
Aug  1 05:46:59 UX kernel: [245695.590843] usb 1-4: USB disconnect, device number 12

```

I'm not sure what's wrong here.

interestingly, lsusb doesn't list a bluetooth device:

```
$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b3d5 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

although for the short period bluetooth doesn't turn off, I get the following:

```
$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b3d5 Chicony Electronics Co., Ltd 
Bus 001 Device 013: ID 13d3:3393 IMC Networks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I'm on ubunut 14.04 LTS

---

