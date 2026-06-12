---
title: "Broadcom BCM2070 Bluetooth 3.0 USB Device not working"
date: 2016-07-22
forum: Hardware
---

### Post by marco. on 2016-07-22
I'm trying to get a Broadcom Bluetooth Adapter working on Ubuntu but when i turn on Bluetooth it only says "Bluetooth is disabled" in the system settings.
Google shows that problems with broadcom devices are common and the usual solution is to extract a proprietary firmware file from the  windows driver (*) but in my case the driver does not specify a firmware file.
So it seems like the device does not require a firmware to be uploaded on boot like many other broadcom devices but it still does not work.
Does anyone has experience with broadcom devices and can help me troubleshoot the problem?

*Examples:
[http://askubuntu.com/questions/632336/bluetooth-broadcom-43142-isnt-working-on-ubuntu?noredirect=1&lq=1](http://askubuntu.com/questions/632336/bluetooth-broadcom-43142-isnt-working-on-ubuntu?noredirect=1&lq=1)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1065400](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1065400)

Here is the output from some commands:

```
uname -a
->
Linux aspire 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


lsusb | grep 21be
-> Bus 008 Device 002: ID 0a5c:21be Broadcom Corp. 


usb-devices
->
T:  Bus=08 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0a5c ProdID=21be Rev=01.00
S:  Manufacturer=Bluetooth v3.0
S:  Product=Bluetooth V3.0BCM2070
C:  #Ifs= 4 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 0 Cls=fe(app. ) Sub=01 Prot=00 Driver=(none)


dmesg
->
[ 5856.164042] usb 8-2: new full-speed USB device number 3 using uhci_hcd
[ 5856.908042] usb 8-2: new full-speed USB device number 4 using uhci_hcd
[ 5857.148993] usb 8-2: New USB device found, idVendor=0a5c, idProduct=21be
[ 5857.148998] usb 8-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 5857.149001] usb 8-2: Product: Bluetooth V3.0BCM2070
[ 5857.149003] usb 8-2: Manufacturer: Bluetooth v3.0
[ 5857.253609] Bluetooth: Core ver 2.21
[ 5857.253970] NET: Registered protocol family 31
[ 5857.253973] Bluetooth: HCI device and connection manager initialized
[ 5857.253978] Bluetooth: HCI socket layer initialized
[ 5857.253982] Bluetooth: L2CAP socket layer initialized
[ 5857.253992] Bluetooth: SCO socket layer initialized
[ 5857.295114] usbcore: registered new interface driver btusb
[ 5857.624770] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[ 5857.624774] Bluetooth: BNEP filters: protocol multicast
[ 5857.624779] Bluetooth: BNEP socket layer initialized


lspci
[does not show bluetooth adapter]


lsmod
Module                  Size  Used by
bnep                   20480  2
btusb                  45056  0
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
btintel                16384  1 btusb
bluetooth             520192  10 bnep,btbcm,btrtl,btusb,btintel
pci_stub               16384  1
vboxpci                24576  0
vboxnetadp             28672  0
vboxnetflt             28672  0
vboxdrv               454656  3 vboxnetadp,vboxnetflt,vboxpci
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
binfmt_misc            20480  1
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         28672  1 uvcvideo
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
v4l2_common            16384  1 videobuf2_v4l2
videodev              176128  4 


hcitool dev
-> Devices: 


hcitool scan
-> Device is not available: No such device


rfkill list
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


iwconfig
->
lo        no wireless extensions.


enp0s25   no wireless extensions.


References to 21be (product id) in btwusb.inf from Windows 10 driver
->
%BRCM21BE.DeviceDesc%=SUSPENDUSB,  USB\VID_0A5C&PID_21BE
BRCM21BE.DeviceDesc="Broadcom BCM2070 Bluetooth 3.0 USB Device"
[seems like the device does not need a rampatch]


hciconfig
->
hci0:    Type: BR/EDR  Bus: USB
    BD Address: 00:1B:10:00:2A:EC  ACL MTU: 1017:8  SCO MTU: 64:0
    DOWN 
    RX bytes:958 acl:0 sco:0 events:38 errors:0
    TX bytes:158 acl:0 sco:0 commands:38 errors:0


hciconfig hci0 up
-> Can't init device hci0: Operation not supported (95)


Ubuntu Bluetooth Settings
-> Bluetooth can only be enabled when the adapter is connected so it seems to be detected

```

---

