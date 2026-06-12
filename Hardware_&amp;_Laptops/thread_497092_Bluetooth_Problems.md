---
title: "Bluetooth Problems"
date: 2007-07-09
forum: Hardware &amp; Laptops
---

### Post by varaonaid on 2007-07-09
Hello,

I'm pulling my hair out trying to get my internal bluetooth working.  I have a Dell e1405 Laptop with the 355 bluetooth adapter.  I've searched the forums, the internet and tried every tip, trick or tutorial I can find.  But my adapter still won't seem to activate.

The bluetooth adapter is internal but seems to be a usb bluetooth adapter nonetheless.  Here's the output of lsusb:

Bus 005 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 017: ID 0a5c:4503 Broadcom Corp.
Bus 002 Device 016: ID 0a5c:4502 Broadcom Corp.
Bus 002 Device 015: ID 0a5c:4500 Broadcom Corp.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000

The results of dmesg also outputs quite a bit of information regarding the bluetooth adapter so I believe it's being detected.   Here's a portion of the output (the whole thing is quite long):

[   23.040000] usb 5-5: device descriptor read/64, error -110
[   23.256000] usb 5-5: new high speed USB device using ehci_hcd and address 4
[   23.936000] ppdev: user-space parallel port driver
[   24.772000] apm: BIOS not found.
[   25.428000] Bluetooth: Core ver 2.11
[   25.428000] NET: Registered protocol family 31
[   25.428000] Bluetooth: HCI device and connection manager initialized
[   25.428000] Bluetooth: HCI socket layer initialized
[   25.452000] Bluetooth: L2CAP ver 2.8
[   25.452000] Bluetooth: L2CAP socket layer initialized
[   26.372000] usb 5-5: device descriptor read/64, error -110
[   41.588000] usb 5-5: device descriptor read/64, error -110
[   41.804000] usb 5-5: new high speed USB device using ehci_hcd and address 5
[   46.824000] usb 5-5: device descriptor read/8, error -110
[   51.944000] usb 5-5: device descriptor read/8, error -110
[   52.160000] usb 5-5: new high speed USB device using ehci_hcd and address 6
[   57.180000] usb 5-5: device descriptor read/8, error -110

[   60.992000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   62.300000] usb 5-5: device descriptor read/8, error -110
[   62.644000] usb 2-1: new full speed USB device using uhci_hcd and address 3
[   62.820000] usb 2-1: configuration #1 chosen from 1 choice
[   62.824000] hub 2-1:1.0: USB hub found
[   62.824000] hub 2-1:1.0: 3 ports detected
[   63.036000] Bluetooth: RFCOMM socket layer initialized
[   63.036000] Bluetooth: RFCOMM TTY layer initialized
[   63.036000] Bluetooth: RFCOMM ver 1.8
[   63.136000] usb 2-1.2: new full speed USB device using uhci_hcd and address 4
[   63.272000] usb 2-1.2: configuration #1 chosen from 1 choice
[   63.476000] usb 2-1.3: new full speed USB device using uhci_hcd and address 5
[   63.612000] usb 2-1.3: configuration #1 chosen from 1 choice
[   63.616000] usbcore: registered new interface driver hiddev
[   63.620000] input: Broadcom Corp as /class/input/input7
[   63.620000] input: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1d.1-1.2
[   63.624000] input: Broadcom Corp as /class/input/input8
[   63.624000] input: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1d.1-1.3
[   63.624000] usbcore: registered new interface driver usbhid
[   63.624000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver

(not sure if the next part is applicable or not):

[  590.804000] usb 2-1: USB disconnect, address 3
[  590.804000] usb 2-1.2: USB disconnect, address 4
[  590.804000] hub 2-1:1.0: cannot reset port 2 (err = -19)
[  590.804000] hub 2-1:1.0: cannot disable port 2 (err = -19)

[  591.676000] input: Broadcom Corp as /class/input/input9
[  591.676000] input: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1d.1-1.2
[  591.880000] usb 2-1.3: new full speed USB device using uhci_hcd and address 8
[  592.012000] usb 2-1.3: configuration #1 chosen from 1 choice
[  592.020000] input: Broadcom Corp as /class/input/input10
[  592.020000] input: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1d.1-1.3
[ 1847.448000] Bluetooth: HCI USB driver ver 2.9
[ 1847.448000] usbcore: registered new interface driver hci_usb
[ 2114.724000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[ 2114.724000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.

[ 2117.380000] usb 2-1: USB disconnect, address 6
[ 2117.380000] usb 2-1.2: USB disconnect, address 7
[ 2117.380000] usb 2-1.3: USB disconnect, address 8

[ 2176.388000] input: Broadcom Corp as /class/input/input11
[ 2176.388000] input: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1d.1-1.2
[ 2176.592000] usb 2-1.3: new full speed USB device using uhci_hcd and address 11
[ 2176.724000] usb 2-1.3: configuration #1 chosen from 1 choice
[ 2176.732000] input: Broadcom Corp as /class/input/input12
[ 2176.732000] input: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1d.1-1.3

[ 8223.540000] usb 2-1: USB disconnect, address 9
[ 8223.540000] usb 2-1.2: USB disconnect, address 10
[ 8223.540000] usb 2-1.3: USB disconnect, address 11

[ 8224.412000] input: Broadcom Corp as /class/input/input13
[ 8224.412000] input: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1d.1-1.2
[ 8224.616000] usb 2-1.3: new full speed USB device using uhci_hcd and address 14
[ 8224.744000] usb 2-1.3: configuration #1 chosen from 1 choice
[ 8224.752000] input: Broadcom Corp as /class/input/input14
[ 8224.752000] input: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1d.1-1.3
[ 8463.136000] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[ 9090.288000] Bluetooth: BNEP (Ethernet Emulation) ver 1.2
[ 9090.288000] Bluetooth: BNEP filters: protocol multicast
[ 9304.196000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[ 9304.196000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
[ 9305.620000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[ 9305.620000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
[ 9307.100000] usb 2-1: USB disconnect, address 12
[ 9307.100000] usb 2-1.2: USB disconnect, address 13
[ 9307.100000] usb 2-1.3: USB disconnect, address 14
[ 9307.340000] usb 2-1: new full speed USB device using uhci_hcd and address 15
[ 9307.516000] usb 2-1: configuration #1 chosen from 1 choice
[ 9307.516000] hub 2-1:1.0: USB hub found
[ 9307.520000] hub 2-1:1.0: 3 ports detected
[ 9307.832000] usb 2-1.2: new full speed USB device using uhci_hcd and address 16
[ 9307.960000] usb 2-1.2: configuration #1 chosen from 1 choice
[ 9307.968000] input: Broadcom Corp as /class/input/input15
[ 9307.968000] input: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1d.1-1.2
[ 9308.172000] usb 2-1.3: new full speed USB device using uhci_hcd and address 17
[ 9308.304000] usb 2-1.3: configuration #1 chosen from 1 choice
[ 9308.308000] input: Broadcom Corp as /class/input/input16
[ 9308.308000] input: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1d.1-1.3

I know that's a lot of info but I tried to just include what seemed applicable to the bluetooth issue.  As you can see, it's detecting my bluetooth adapter.  I've tried the hciconfig hcio reset (also tried hci1) but I get the same response each time:

Can't get device info: No such device

and from hcitool dev
Devices:

I've installed all the bluetooth apps including the bluez-firmware which some Broadcom bluetooth adapters require.  I've also started all the recommended modules using modprobe hci_usb, etc.  It seems the only thing I can't do is to somehow get (k)ubuntu to actually turn the device on.

If anyone can give me any assistance on this, I would be SO appreciative!  If you need any additional system or output information, please let me know.  Thanks in advance!!

---

### Post by GNUser on 2007-07-25
I have pretty much the same problem, same device, same hciconfig output, similar dmesg output. Only difference is that I have an Inspiron 1420... So, sorry if this has been solved somewhere else, but I'd like to see what might be the issue here (never used bluetooth before)

---

### Post by timothyM on 2007-07-25
Hello,

I also have a broadcom chip in the form of a usb dongle (a Belkin F8T001). In every other ubuntu I have only had to install the bluetooth packages and the firmware for it, and then it has just worked.

For Feisty I have put the firmware (BCM2033-FW.bin and BCM2033-MD.hex from the bluez website) in /lib/firmware. But now I am in the same situation as you, with the device being recognised by the system, but seemingly not creating a device for it.

Other posts have recommended:

```
$sudo hciconfig hci0 reset
```

but when I run that I get:
```

Can't get device info: No such device
```

Any one have any ideas?

Timothy

---

### Post by lalada on 2007-08-21
Maybe solution of this problem was found? ](*,)

---

### Post by fcastillo on 2007-08-25
I have exactly the same problem, my internal Bluetooth device is not recognized. However, if i connect an USB Bluetooth, my laptop recognized it, and i can use it without a problem.

---

### Post by jegb on 2008-05-19
answer may be here:
[http://wiki.bluez.org/wiki/HOWTO/InputDevices](http://wiki.bluez.org/wiki/HOWTO/InputDevices)

---

### Post by ccw127 on 2008-05-20
I took a look at the links on this thread and found that none of them really helped with the (seemingly similar) problem we are having. After a while, getting tired of reading, I just headed into synaptic and looked around there. After installing a couple of packages that didn't seem to be all that important(but not installed), and a reboot, Bluetooth came up just fine.

Here are the packages that I installed(That I can remember):
--All the bluez packages (minus cups and pcmcia)
--Most of the packages having to do with multisync (I can't remember if I did this before or after bluetooth started working
--bluetooth and libbluetooth2 (I can't remember if I did these or they were already there)
--libbtctl4
--libgnomebt0

Again, I am not sure which packages were installed by default since the system noticed I had Bluetooth when I first installed, and which ones I did. If anyone wants more details of my installed packages, let me know and I will be more than happy to hook you up.

Chris
[email]hololight@gmail.com[/email]

---

