---
title: "Bluetooth not working 18.04 - Broadcom BCM2046B1"
date: 2019-01-17
forum: Hardware
---

### Post by steve234 on 2019-01-17
Hi there,

I've done an hour or so of googling and searching here, but Im struggling to get bluetooth up and running on a Dell XPS 1530 laptop running Lubuntu 18.04 (fresh install).  The laptop has a terrible trackpad so I'd like to connect my BT mouse.

The bluetooth applet (I'm not sure which one ships with Lubuntu) in the bar says "no Bluetooth Adaptor Found".

If I run blueman-applet separately it seems to allow me to turn Bluetooth on and off but says "no adaptors found" when I try to add a device.

Output of $ sudo lsusb |grep Bluetooth is:

```
$ sudo lsusb |grep Bluetooth
Bus 007 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)

```

Any ideas what I can try as a next step?

---

### Post by jeremy31 on 2019-01-17
Post results for ```
lsusb; dmesg | egrep -i 'blue|firm'
```

---

### Post by steve234 on 2019-01-17
Hi @jeremy31

The output is:

```
$ lsusb; dmesg | egrep -i 'blue|firm'Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 004: ID 0a5c:4503 Broadcom Corp. Mouse (Boot Interface Subclass)
Bus 007 Device 003: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 007 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0483:2016 STMicroelectronics Fingerprint Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[    0.137104] acpi PNP0A03:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    7.165634] iwl3945 0000:0b:00.0: loaded firmware version 15.32.2.9
[   11.044068] iwl3945 0000:0b:00.0: Enabling power save might cause firmware crashes

```

---

### Post by jeremy31 on 2019-01-17
steve234, see if my old answer at [https://askubuntu.com/a/583167/300665](https://askubuntu.com/a/583167/300665) still works

---

### Post by steve234 on 2019-01-17
thanks,

I tried both the =c0 and =a0 versions - no dice

my current /etc/udev/rules.d/60-bluetooth-hid2hci.rules is:

```
#udev rules fÃ¼r Lenovo Ideacentre Bluetooth

ACTION=="remove", GOTO="idea_end"
SUBSYSTEM!="usb", GOTO="idea_end"


# Variety of Broadcom Bluetooth devices - match on a mouse device that is
# self powered and where a HID report needs to be sent to switch modes
# Known supported devices: 0a5c:4503


ATTR{bInterfaceClass}=="03", ATTR{bInterfaceSubClass}=="01", ATTR{bInterfaceProtocol}=="02", \
  ATTRS{bDeviceClass}=="00", ATTRS{idVendor}=="0a5c", ATTRS{bmAttributes}=="c0", \
  RUN+="hid2hci --method=dell --devpath=%p", ENV{HID2HCI_SWITCH}="1"


LABEL="idea_end"



```

Did I do something wrong?

---

### Post by jeremy31 on 2019-01-17
Your device might be different, post results for ```
sudo cat /sys/kernel/debug/usb/devices | grep Vendor=0a5c -A8
```

---

### Post by steve234 on 2019-01-17
I was just reading that in the previous answer but was not sure what it did. Her you go:

```
$ sudo cat /sys/kernel/debug/usb/devices | grep Vendor=0a5c -A8P:  Vendor=0a5c ProdID=4500 Rev= 1.00
S:  Manufacturer=Broadcom
S:  Product=BCM2045B2
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   1 Ivl=255ms


T:  Bus=07 Lev=02 Prnt=02 Port=01 Cnt=01 Dev#=  3 Spd=12   MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0a5c ProdID=4502 Rev= 1.00
S:  Manufacturer=Broadcom Corp
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms


T:  Bus=07 Lev=02 Prnt=02 Port=02 Cnt=02 Dev#=  4 Spd=12   MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0a5c ProdID=4503 Rev= 1.00
S:  Manufacturer=Broadcom Corp
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   4 Ivl=10ms

```

---

### Post by steve234 on 2019-01-17
Additionally, when I check the bluetooth status I get:

```
$ systemctl status bluetooth.service&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset
   Active: inactive (dead)
Condition: start condition failed at Thu 2019-01-17 12:07:58 GMT; 36s ago
           &#9492;&#9472; ConditionPathIsDirectory=/sys/class/bluetooth was not met
     Docs: man:bluetoothd(8)



```

---

### Post by jeremy31 on 2019-01-17
Use ATTRS{bmAttributes}=="e0", in the file and reboot as the c0 doesn't match

---

### Post by steve234 on 2019-01-17
Cheers:

Sorry, I did change back to e0 after I posted the code. 

The fix for me was Windows based. I needed to reflash the Dell 335 chip's firmware as described here:

[https://www.dell.com/community/Networking-Internet-Bluetooth/Dell-XPS-M1530-Bluetooth-355-and-Windows-7/td-p/3217683](https://www.dell.com/community/Networking-Internet-Bluetooth/Dell-XPS-M1530-Bluetooth-355-and-Windows-7/td-p/3217683)

I now worry that if I accidentally turn off the Wifi switch (due to its location I do alllll the tiiiiime!) which also controls the BT adaptor, I'll have to head back to Windows and re-install the driver - fingers crossed

---

### Post by jeremy31 on 2019-01-17
I wouldn't worry about it as I think the Window's fix does the same thing that my fix should do

---

