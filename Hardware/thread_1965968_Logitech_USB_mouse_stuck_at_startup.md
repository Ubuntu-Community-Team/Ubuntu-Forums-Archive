---
title: "Logitech USB mouse stuck at startup"
date: 2012-04-26
forum: Hardware
---

### Post by argail1980 on 2012-04-26
Hi,

I just installed 12.04 beta and it is mostly working fine. However, my mouse is not working after startup. I'm using gnome shell on ubuntu 12.04 64bit. The mouse is some generic optical logitech mouse (M-BT58 )

I found some stuff about unloading and reloading the usbhid module on google, but it doesn't work. lsusb does not show the mouse until I unplug it and plug it back in.

I tried

```
sudo -s
rmmod usbhid
modprobe usbhid
```

lsusb output at startup (no matter if i reloaded the module or not):
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 07b8:e004 AboCom Systems Inc Mass Storage Device
Bus 002 Device 002: ID 04d9:1603 Holtek Semiconductor, Inc. Keyboard

```
and after unplugging the mouse for a second...
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 07b8:e004 AboCom Systems Inc Mass Storage Device
Bus 002 Device 002: ID 04d9:1603 Holtek Semiconductor, Inc. Keyboard
Bus 002 Device 003: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse (M-BT58)

```
there it is and works. I find it kind of annoying to unplug the mouse at every reboot... 

Thanks in advance for any ideas

argail

---

### Post by nclavaud on 2012-05-01
Hey, got the same exact problem, with the same exact mouse model. The cursor is stuck in the middle of the desktop after startup and I have to unplug the mouse and plug it in again to make it work.

However:
 - I am running Ubuntu 64bits;
 - I remember having the same exact problem with previous LTS release (10.04) involving the same mouse, but I don't remember how I solved it;
 - sometimes, the mouse works well and I don't need to unplug/plug it back.

Before unplugging:
```
> lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 046d:08ce Logitech, Inc. QuickCam Pro 5000
Bus 002 Device 002: ID 056a:00d4 Wacom Co., Ltd
```

After plugging it back in:
```
> lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 046d:08ce Logitech, Inc. QuickCam Pro 5000
Bus 002 Device 002: ID 056a:00d4 Wacom Co., Ltd 
Bus 002 Device 003: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse (M-BT58)

> dmesg | tail
[ 1435.680042] usb 2-2: new low-speed USB device number 3 using ohci_hcd
[ 1435.904710] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:0b.0/usb2/2-2/2-2:1.0/input/input6
[ 1435.904940] generic-usb 0003:046D:C03E.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:0b.0-2/input0
```

---

### Post by pt123 on 2012-05-29
I have similar issues with a logitech mouse Bus 002 Device 005: ID 046d:c043 Logitech, Inc. MX320/MX400 Laser Mouse

Like others this was my device 5, i think it has do with IRQ conficts

---

### Post by pt123 on 2012-05-29
I have added a bug report

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1006145](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1006145)

if this affects you please mark it as such

---

### Post by OostAchterhoek on 2012-06-01
Hello,

Unplugging and plugging in again the usb Logitech Unifying receiver make work the wireless mouse and keyboard (Logitech) like it should.

So following solution did work for me:

add following lines to /etc/rc.local

modprobe -r hid_logitech_dj 
modprobe hid_logitech_dj


For me this solution did work fine.
Good luck!;)

---

### Post by jrioublanc on 2012-06-07
> **nclavaud said:**
> ... I remember having the same exact problem with previous LTS release (10.04) involving the same mouse, but I don't remember how I solved it ...

Yes I got this issue too with 12.04 and with 10.04, only the upgrade to 10.10 fixed it!

Thanks **pt123**  let's wait the results of the bug report

---

