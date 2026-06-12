---
title: "Reset USB Device"
date: 2011-11-25
forum: Hardware
---

### Post by dk_zero-cool on 2011-11-25
Hi.
I got my self a USB Wireless network Adaptor. The device is a NETGEAR N-300 (WNA3100) with a broadcom chip. Like most wireless devices, it only has windows drivers and needs to be run via NDISWrapper. Unlike most of the devices I have had, it does this quite good, but I still have one problem.

The device aparently has 3 states. On/Off and some sort of Standby (Half on and half off). When I turn on my computer, the device is off. If I then remove the device and plug it back in, it get's in this standby state. However, it will not turn on. The only way to turn it on is to re-install the driver using ndisgtk. Using ndiswrapper in a console will not work.

It seams that ndisgtk does some kind of action after installing the driver that wakes up the device. ndiswrapper does not and neither does dbus.

I have included the dmesg of the actions taken from boot and until the device is up and running.

```
# THE COMPUTER HAS JUST BOOTED. THERE IS NO LIGHT IN THE DEVICE INDICATOR LAMP.
[    1.204059] usb 1-8: new high speed USB device number 4 using ehci_hcd

# I PULL OUT THE DEVICE AND PUT IT BACK IN. NOW THERE IS A TINY STANDBY LIGHT.
[  160.189668] usb 1-8: USB disconnect, device number 4
[  288.384095] usb 1-8: new high speed USB device number 5 using ehci_hcd
[  289.640153] usb 1-8: usbfs: USBDEVFS_CONTROL failed cmd mtp-probe rqt 128 rq 6 len 1024 ret -110

# I REMOVE THE NDIS DRIVER AND REINSTALL IT. THE DEVICE LIGHTS UP REAL BRIGHT.
[  167.089705] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[  167.220067] usb 1-8: reset high speed USB device number 5 using ehci_hcd
[  167.355192] ndiswrapper (import:233): unknown symbol: ntoskrnl.exe:'IoUnregisterPlugPlayNotification'
[  167.355402] ndiswrapper: driver bcmwlhigh5 (Netgear,11/05/2009, 5.60.180.11) loaded
[  167.940026] wlan0: ethernet device c4:3d:c7:cc:14:6f using NDIS driver: bcmwlhigh5, version: 0x53cb40b, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9020.F.conf
[  167.943823] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  167.945153] usbcore: registered new interface driver ndiswrapper
[  167.966839] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  178.151594] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  178.892777] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  189.360048] wlan0: no IPv6 routers present
```

I have also included an 'lsusb' overview of the device in question.

```
Device: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            3.00
  iManufacturer           3 Linux 3.0.0-12-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:1d.3
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
	bLength                 7
	bDescriptorType         5
	bEndpointAddress     0x81  EP 1 IN
	bmAttributes            3
	  Transfer Type            Interrupt
	  Synch Type               None
	  Usage Type               Data
	wMaxPacketSize     0x0002  1x 2 bytes
	bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled
```

My question is this. I don't know if this is something that dbus, ndiswrapper or whatever should do when the device is plugged-in or the computer is booting. But what is it ndisgtk does that ndiswrapper does not to wake up the device? And how can I get dbus to do it whenever the device is plugged-in?

---

### Post by dk_zero-cool on 2011-11-25
He he, this is embarrassing. The ndiswrapper module was not set to be loaded during boot. Thats what ndisgtk did when I installed the driver :p

It should have been the first I should have thought of.

---

