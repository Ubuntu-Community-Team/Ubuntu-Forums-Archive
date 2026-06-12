---
title: "usbfs error setting config, causes usb errors"
date: 2012-12-20
forum: Hardware
---

### Post by Slates on 2012-12-20
I can see many posts on this topic, but Im not clear what the root cause is, or what is happening here. So Ive been unable to solve it, any pointers of where I might look would be great. 

I am running a vekkeman k8055 board off a usb hub which is shared with two USB disk drives. The board isnt really the subject here, interfacing with usb devices and diagnosing associated errors is.

With this board on 64 bit Ubuntu 12.04, I have it up and running and can fully control the board. However when I set a port (ie issue a command to the board to set, say port 1 on), the operation works, but when I reset the port back to 0 it causes the two USB disk drives on the same usb hub to unmount. 

Looking at the logs I can see the following error (which also occurs if the device is connected exclusively to a usb port, ie without a hub) :
> 
usbfs: interface 0 claimed by usbfs while 'k8055' sets config #1
and the two usb disk drives sharing the hub report :

> Dec 21 11:58:23 Gonzalez kernel: [ 1030.592063] usb 4-2: USB disconnect, device number 3
Dec 21 11:58:28 Gonzalez kernel: [ 1036.040035] usb 4-2: new low-speed USB device number 4 using uhci_hcd
Dec 21 11:58:28 Gonzalez mtp-probe: checking bus 4, device 4: "/sys/devices/pci0000:00/0000:00:1a.1/usb4/4-2"
Dec 21 11:58:28 Gonzalez mtp-probe: bus: 4, device: 4 was not an MTP device
Dec 21 11:58:28 Gonzalez kernel: [ 1036.227670] generic-usb 0003:10CF:5502.000B: hiddev0,hidraw2: USB HID v1.00 Device [Velleman  USB K8055] on usb-0000:00:1a.1-2/input0
Dec 21 11:58:35 Gonzalez kernel: [ 1043.240073] usb 4-2: USB disconnect, device number 4
Dec 21 12:00:01 Gonzalez CRON[5083]: (root) CMD (/usr/local/lib/sa/sa1 1 1)
Dec 21 12:00:54 Gonzalez kernel: [ 1181.900148] usb 2-4.1.4: new low-speed USB device number 29 using ehci_hcd
Dec 21 12:00:54 Gonzalez kernel: [ 1182.015740] generic-usb 0003:10CF:5502.000C: hiddev0,hidraw2: USB HID v1.00 Device [Velleman  USB K8055] on usb-0000:00:1d.7-4.1.4/input0
Dec 21 12:00:54 Gonzalez mtp-probe: checking bus 2, device 29: "/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1.4"
Dec 21 12:00:54 Gonzalez mtp-probe: bus: 2, device: 29 was not an MTP device
The obvious first  workaround is to try without a usb hub, but not only does this not identify or solve the root cause, but in my case is difficult because I'm using a (single) 10foot usb extension. As I also note, the inderlying error remains so I also couldnt be sure that this  error isnt going to cause other problems and/or unreliable operation.

Does anyone know what is actually going on here, or where I might better ask this question? Is this an addressing error, ownership, a bug - or something else.

PS although the device itself isnt directly relevant to this problem in my opinion, if anyone is familiar with the k8055 I have correctly set permissions and can execute the commands without the use of root (this was one of the many fixes suggested that didnt work for me).

many thanks

---

