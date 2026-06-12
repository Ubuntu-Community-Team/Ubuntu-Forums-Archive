---
title: "USB automount of Android problem, UDEV rules not working"
date: 2014-04-09
forum: Hardware
---

### Post by hallansing on 2014-04-09
linux 10.10 64 bit 

for those that know  udev programming rules: 

trying to automount my Android phone through UDEV rules, created 3 simple TEST rules, 
which basically play different sounds when phone connect and disconnects:
1st line defines device 
2nd line works on CONNECT or add device - and it works fine 
3rd line works on DISCONNECT or remove device  - and it does not work, that's the problem ***

ATTR{idVendor}=="04e8",  ATTR{idProduct}=="6860", GROUP="plugdev", SYMLINK+="libmtp-%k",  ENV{ID_MTP_DEVICE}="1", ENV{ID_MEDIA_PLAYER}="1"

ENV{ID_MODEL}=="Galaxy_Nexus",  ENV{ID_MODEL_ID}=="6860", ACTION=="add", RUN+="/usr/bin/play -q  /home/val/valscripts/device_connect.ogg"

# this is the problem rule ...
ENV{ID_MODEL}=="Galaxy_Nexus",  ENV{ID_MODEL_ID}=="6860", ACTION=="remove", RUN+="/usr/bin/play -q  /home/val/valscripts/device_disconnect.ogg"

there  is nothing wrong with syntax or sound flies, verified...  

udev add:

UDEV  [1396910673.052949] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1 (usb)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1
SUBSYSTEM=usb
DEVNAME=/dev/bus/usb/002/048
DEVTYPE=usb_device
PRODUCT=4e8/6860/216
TYPE=0/0/0
BUSNUM=002
DEVNUM=048
SEQNUM=4510
ID_VENDOR=samsung
ID_VENDOR_ENC=samsung
ID_VENDOR_ID=04e8
ID_MODEL=Galaxy_Nexus
ID_MODEL_ENC=Galaxy\x20Nexus
ID_MODEL_ID=6860
ID_REVISION=0216
ID_SERIAL=samsung_Galaxy_Nexus_0149BD301701000C
ID_SERIAL_SHORT=0149BD301701000C
ID_BUS=usb
ID_USB_INTERFACES=:ffff00:ff4201:
ID_MTP_DEVICE=1
ID_MEDIA_PLAYER=1
MAJOR=189
MINOR=175
DEVLINKS=/dev/char/189:175 /dev/libmtp-2-1.1

UDEV  [1396910673.055461] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0 (usb)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0
SUBSYSTEM=usb
DEVTYPE=usb_interface
PRODUCT=4e8/6860/216
TYPE=0/0/0
INTERFACE=255/255/0
MODALIAS=usb:v04E8p6860d0216dc00dsc00dp00icFFiscFFip00
SEQNUM=4511

udev remove:

UDEV  [1396910637.004780] remove   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.1 (usb)
UDEV_LOG=3
ACTION=remove
DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.1
SUBSYSTEM=usb
DEVTYPE=usb_interface
PRODUCT=4e8/6860/216
TYPE=0/0/0
INTERFACE=255/66/1
MODALIAS=usb:v04E8p6860d0216dc00dsc00dp00icFFisc42ip01
SEQNUM=4508

UDEV  [1396910637.004869] remove   /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1 (usb)
UDEV_LOG=3
ACTION=remove
DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1
SUBSYSTEM=usb
DEVNAME=/dev/bus/usb/002/023
DEVTYPE=usb_device
PRODUCT=4e8/6860/216
TYPE=0/0/0
BUSNUM=002
DEVNUM=023
SEQNUM=4509
ID_VENDOR=samsung
ID_VENDOR_ENC=samsung
ID_VENDOR_ID=04e8
ID_MODEL=Galaxy_Nexus
ID_MODEL_ENC=Galaxy\x20Nexus
ID_MODEL_ID=6860
ID_REVISION=0216
ID_SERIAL=samsung_Galaxy_Nexus_0149BD301701000C
ID_SERIAL_SHORT=0149BD301701000C
ID_BUS=usb
ID_USB_INTERFACES=:ffff00:ff4201:
ID_MTP_DEVICE=1
ID_MEDIA_PLAYER=1
MAJOR=189
MINOR=150
DEVLINKS=/dev/char/189:150 /dev/libmtp-2-1.1

both add and remove events in udev seem to generate proper attributes 

however the 2nd rule REMOVE is not firing ... 

any clues, suggestions, help much appreciated... 

regards.

---

