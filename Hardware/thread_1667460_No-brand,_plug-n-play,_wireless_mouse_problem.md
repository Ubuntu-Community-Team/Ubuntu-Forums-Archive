---
title: "No-brand, plug-n-play, wireless mouse problem"
date: 2011-01-14
forum: Hardware
---

### Post by Limmor on 2011-01-14
Hi all,

I bought a no-brand wireless mouse and have trouble making it work in Ubuntu 10.10. It works fine Windows XP, just by plugging in in Windows XP. I am fairly new to Ubuntu, so if you care to explain briefly what is happening in the solution steps, I'll be happy to learn ;) Information:

- Works plug-n-play in Windows XP.

Something is detected when I plug in the wireless adapter, but these devices disappear after a couple of seconds:

# lsusb: Bus 003 Device 058: ID 0603:1031 Novatek Microelectronics Corp; keeps reappearing when adapter is plugged in.
# ls /dev/input: mouse1 appears briefly.
# ls /dev/input/by-id: usb-SINO_WEALTH_SINO_WEALTH-mouse.
# ls /dev: hidraw0 appears briefly.
# cat /dev/hidraw0: Input/output error.
# xinput --list: SINO WEALTH SINO WEALTH id=14	[slave  pointer (2)]

---

### Post by Dr_Frost on 2011-08-22
I just got a mouse with the same wireless chip and can confirm that it works in XP, but not 10.10.

Anybody got any idea's?

[http://www.dealextreme.com/p/2-4ghz-wireless-500-1000dpi-usb-optical-mouse-w-receiver-black-1-x-aa-81144](http://www.dealextreme.com/p/2-4ghz-wireless-500-1000dpi-usb-optical-mouse-w-receiver-black-1-x-aa-81144)

---

### Post by luisfpg on 2011-12-12
Same here...
Bought the same mouse, and it still doesn't work for 11.10.
It just gets connected and disconnected. Here is a partial listing of dmesg:
```

[ 8657.570511] usb 2-1.1: new low speed USB device number 102 using ehci_hcd
[ 8657.689111] input: SINO WEALTH SINO WEALTH as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input112
[ 8657.689423] generic-usb 0003:0603:1031.0066: input,hiddev0,hidraw1: USB HID v1.11 Mouse [SINO WEALTH SINO WEALTH] on usb-0000:00:1d.0-1.1/input0
[ 8657.908762] usb 2-1.1: USB disconnect, device number 102
[ 8658.149522] usb 2-1.1: new low speed USB device number 103 using ehci_hcd
[ 8658.269703] input: SINO WEALTH USBSINALTH as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input113
[ 8658.270192] generic-usb 0003:0603:1031.0067: input,hiddev0,hidraw1: USB HID v1.11 Mouse [SINO WEALTH USBSINALTH] on usb-0000:00:1d.0-1.1/input0
[ 8658.270722] usb 2-1.1: USB disconnect, device number 103
[ 8658.580816] usb 2-1.1: new low speed USB device number 104 using ehci_hcd
[ 8658.698205] input: SINO WEALTH SINO WEALTH as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input114
[ 8658.698654] generic-usb 0003:0603:1031.0068: input,hiddev0,hidraw1: USB HID v1.11 Mouse [SINO WEALTH SINO WEALTH] on usb-0000:00:1d.0-1.1/input0
[ 8658.930977] usb 2-1.1: USB disconnect, device number 104
[ 8659.219654] usb 2-1.1: new low speed USB device number 105 using ehci_hcd
[ 8659.336686] input: SINO WEALTH SINO WEALTH as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input115
[ 8659.336946] generic-usb 0003:0603:1031.0069: input,hiddev0,hidraw1: USB HID v1.11 Mouse [SINO WEALTH SINO WEALTH] on usb-0000:00:1d.0-1.1/input0
[ 8659.337378] usb 2-1.1: USB disconnect, device number 105
[ 8659.618975] usb 2-1.1: new low speed USB device number 106 using ehci_hcd
[ 8659.736696] input: SINO WEALTH SINO WEALTH as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input116
[ 8659.737017] generic-usb 0003:0603:1031.006A: input,hiddev0,hidraw1: USB HID v1.11 Mouse [SINO WEALTH SINO WEALTH] on usb-0000:00:1d.0-1.1/input0
[ 8659.953207] usb 2-1.1: USB disconnect, device number 106
[ 8660.213957] usb 2-1.1: new low speed USB device number 107 using ehci_hcd
[ 8660.330889] input: SINO WEALTH USBSINALTH as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input117
[ 8660.331362] generic-usb 0003:0603:1031.006B: input,hiddev0,hidraw1: USB HID v1.11 Mouse [SINO WEALTH USBSINALTH] on usb-0000:00:1d.0-1.1/input0
[ 8660.333062] usb 2-1.1: USB disconnect, device number 107

```

Any ideas?

---

### Post by quenomin on 2011-12-12
I bought a no-brand wireless mouse and have trouble making it work in  Ubuntu 10.10. It works fine Windows XP, just by plugging in in Windows  XP. I am fairly new to Ubuntu, so if you care to explain briefly what is  happening in the solution steps.
[custom labels](http://www.progressiveint.com)
[labels and stickers](http://www.progressiveint.com)

---

### Post by fedaykin42 on 2012-05-28
After a little usbmon sniffing and some kernel header file reading I was able to solve this problem (kernel 2.6.38-1-generic on Ubuntu 11.04).  The SINO WEALTH USB HID device does not like having reports read during initialization.  This causes a protocol error and the kernel's USB HID support or the core ends up resetting the device and the cycle continues.  To resolve the problem, create a module options file and declare some quirks for usbhid:

Create the file /etc/modprobe.d/usb-hid.conf and add the following line:

[FONT=Courier New][SIZE=1]options usbhid quirks=0x0603:0x1031:0x20000000[/SIZE][/FONT]
 
Note that 0603 is the USB VID and 1031 is the USB PID for the device.  These were taken from my mouse.  Yours may be different.  You can quickly find out this information by looking at dmesg output (red highlight):
 
[FONT=Courier New][SIZE=1]May 28 10:39:51 lothlorien kernel: [   87.690092] usb 2-1: new low speed USB device using uhci_hcd and address 2[/SIZE][/FONT]
[FONT=Courier New][SIZE=1]May 28 10:39:51 lothlorien kernel: [   87.891942] input: SINO WEALTH SINO WEALTH as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input11[/SIZE][/FONT]
[FONT=Courier New][SIZE=1]May 28 10:39:51 lothlorien kernel: [   87.892272] generic-usb 0003:[COLOR=#ff0000]0603:1031[/COLOR].0004: input,hiddev0,hidraw3: USB HID v1.11 Mouse [SINO WEALTH SINO WEALTH] on usb-0000:00:1d.0-1/input0[/SIZE][/FONT]
  
The value 0x20000000 comes from the USB HID quirks defined in include/linux/hid.h:
 
[FONT=Courier New][SIZE=1]#define HID_QUIRK_NO_INIT_REPORTS               0x20000000[/SIZE][/FONT]
   
Good luck!

---

### Post by Dr_Frost on 2012-06-25
I added the usbhid but mine still loops like crazy.
Do i need to do anything else, haven&#8217;t restarted or anything.
So far i just created the file and added the quirks line

Using 12.04, MATE Desktop, Kernel 3.2.0-25-generic-pae

> 
[155837.656078] usb 3-1: new low-speed USB device number 38 using uhci_hcd
[155837.876567] input: SINO WEALTH SINO WEALTH as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input304
[155837.877597] generic-usb 0003:0603:1031.0122: input,hiddev0,hidraw2: USB HID v1.11 Mouse [SINO WEALTH SINO WEALTH] on usb-0000:00:1d.1-1/input0
[155838.408120] usb 3-1: USB disconnect, device number 38
[155839.144135] usb 3-1: new low-speed USB device number 39 using uhci_hcd
[155839.364483] input: SINO WEALTH SINO WEALTH as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input305
[155839.365243] generic-usb 0003:0603:1031.0123: input,hiddev0,hidraw2: USB HID v1.11 Mouse [SINO WEALTH SINO WEALTH] on usb-0000:00:1d.1-1/input0
[155839.896114] usb 3-1: USB disconnect, device number 39
Note: dmesg was just a small outprint, it has already gone through about 200 "devices"

---

### Post by fedaykin42 on 2012-07-12
Yes, you need to either reload the USB HID module or reboot the machine.

---

