---
title: "USB joystick with Linux only works when I disconnected and reconnected its"
date: 2010-02-09
forum: Hardware
---

### Post by offox on 2010-02-09
HI!

USB joystick with Linux only works when I disconnected and reconnected its.

I have a problem that it can easy, but I didn't find a solution yet.

When I turn on my computer using a Ubuntu and tried to use the joystick the commands of joystick doesn't pass to SO. Once I disconnect and reconnect the joystick on USB port it pass to work.

Environment:

SO: Debian 8.04 LTS

dmesg - relevants part only:

[   26.560703] usb 8-2: configuration #1 chosen from 1 choice
[   26.573659] usbcore: registered new interface driver hiddev
[   26.591720] input: HID 04d9:1400 as /devices/pci0000:00/0000:00:1d.2/usb8/+8-1/8-1:1.0/input/input1
[   26.606420] input,hidraw0: USB HID v1.10 Keyboard [HID 04d9:1400] on usb-0+000:00:1d.2-1
[   26.634671] input: HID 04d9:1400 as /devices/pci0000:00/0000:00:1d.2/usb8/+8-1/8-1:1.1/input/input2
[   26.671260] input,hidraw1: USB HID v1.10 Mouse [HID 04d9:1400] on usb-0000+:00:1d.2-1
[   26.686364] input: CH PRODUCTS Megatron OEM 2 Axis 1 Button Joystick as /d+evices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.0/input/input3
[   26.686376] input,hidraw2: USB HID v1.00 Joystick [CH PRODUCTS Megatron OE+M 2 Axis 1 Button Joystick] on usb-0000:00:1d.2-2
[   26.686385] usbcore: registered new interface driver usbhid
[   26.686387] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6+:USB HID core driver

...

[  683.610080] usb 8-2: USB disconnect, address 4
[  688.303698] usb 8-2: new low speed USB device using uhci_hcd and address 5
[  688.482776] usb 8-2: configuration #1 chosen from 1 choice
[  688.506691] input: CH PRODUCTS Megatron OEM 2 Axis 1 Button Joystick as /d+evices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.0/input/input8
[  688.551108] input,hidraw2: USB HID v1.00 Joystick [CH PRODUCTS Megatron OE+M 2 Axis 1 Button Joystick] on usb-0000:00:1d.2-2

/proc/bus/input/devices:

I: Bus=0003 Vendor=068e Product=00af Version=0100
N: Name="CH PRODUCTS Megatron OEM 2 Axis 1 Button Joystick"
P: Phys=usb-0000:00:1d.2-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.0/input/input8
U: Uniq=
H: Handlers=event3 js0*
B: EV=1b
B: KEY=1 0 0 0 0 0 0 0 0 0
B: ABS=3
B: MSC=10

Device: /dev/input/js0

I used to test cat /dev/input/js0 and my application.

I tried to access remotely with ssh, because my keyboard use USB port too, and executed the commands down:

# modprobe -r joydev
# modprobe -r usbhid
# modprobe usbhid
# modprobe joydev

The joystick doesn't work after I execute commands above.

What is happening?

Help me!

---

### Post by ambawell on 2010-06-09
Do a lsmod and see if UHCI is a module.
If it is try to modprobe -r UHCI then modprobe UHCI
If that works you can write in you start up script. /etc/init.d/rc.local should work.

---

