---
title: "irDa"
date: 2005-11-29
forum: Hardware &amp; Laptops
---

### Post by obelix0 on 2005-11-29
Hi ! I have a pbl with my USB irDa XPC-RC01 :confused: 

I installed "sudo apt-get install irda-utils ircp" and

I don't how to set this file "sudo gedit /etc/default/irda-utils" wit hthe good device.


I connect my IrDa on my USB conenction on the laptop but I haven't got any conenction with my phone. I have already a USB mouse connected.

I tried without succes this commands :

sudo dmesg | grep irda
[4299312.208000] irda_init()


mknod /dev/ircomm0 c 161 0



thank's for help !

Obé

---

### Post by obelix0 on 2005-11-30
ok maybe I was not enough clear :(

I have an irDA Box that I connect to the USB port of my laptop.

How I can configure it ?

thank's for help :smile:

---

### Post by johannes on 2005-12-01
I wrote [this]("http://www.ubuntuforums.org/showpost.php?p=504374&postcount=2") in some other thread. I'm not sure if it will work for you, but it might be worth a shot. If it works it will set up your irda port and tell how to send files to/from your computer using the console.

If it doesn't work, then post the output from irdadump (if any) and I'll try to help.

---

### Post by obelix0 on 2005-12-05
sorry I'm late to reply :D 

so it doesn't work... irdadump show nothing ! :confused: 

but don't forget that my irda is a box that I plug into the USB port


thank's for help

Obe

---

### Post by johannes on 2005-12-07
What does "dmesg | grep usb" show?

---

### Post by obelix0 on 2005-12-07
Thank's to help me...

I have a USB mouse connected to my laptop !

Whithout the USB box connected when I start my laptop :
[4294678.142000] usbcore: registered new driver usbfs
[4294678.142000] usbcore: registered new driver hub
[4294678.374000] usb 1-2: new low speed USB device using uhci_hcd and address 2
[4294679.100000] usb 1-2: USB disconnect, address 2
[4294679.266000] usb 1-2: new low speed USB device using uhci_hcd and address 3
[4294681.008000] usbcore: registered new driver hiddev
[4294681.030000] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-2
[4294681.030000] usbcore: registered new driver usbhid
[4294681.030000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver

With the USB box connected when I start my laptop :
[4294678.210000] usbcore: registered new driver usbfs
[4294678.210000] usbcore: registered new driver hub
[4294678.443000] usb 1-2: new low speed USB device using uhci_hcd and address 2
[4294678.908000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[4294679.324000] usb 1-2: USB disconnect, address 2
[4294679.490000] usb 1-2: new low speed USB device using uhci_hcd and address 3
[4294679.778000] usb 2-1: new low speed USB device using uhci_hcd and address 3
[4294681.077000] usbcore: registered new driver hiddev
[4294681.099000] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-2
[4294681.244000] input,hiddev96: USB HID v1.10 Keyboard [13ec:0006] on usb-0000:00:1d.1-1
[4294681.244000] usbcore: registered new driver usbhid
[4294681.244000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver


In /var/log/syslog when I plug the USB box :
Dec  7 18:09:21 localhost kernel: [4295874.886000] usb 2-1: new low speed USB device using uhci_hcd and address 2
Dec  7 18:09:21 localhost kernel: [4295875.179000] input,hiddev96: USB HID v1.10 Keyboard [13ec:0006] on usb-0000:00:1d.1-1
Dec  7 18:09:21 localhost hal.hotplug[8793]: DEVPATH is not set (subsystem input)
Dec  7 18:09:21 localhost input.agent[8794]:      evdev: already loaded
Dec  7 18:09:21 localhost usb.agent[8800]:      usbhid: already loaded
Dec  7 18:09:22 localhost input.agent[8863]:      evdev: already loaded

When I unplug the USB box :
Dec  7 18:10:21 localhost kernel: [4295935.063000] usb 2-1: USB disconnect, address 2
Dec  7 18:10:21 localhost hal.hotplug[8932]: DEVPATH is not set (subsystem input)

---

### Post by obelix0 on 2005-12-14
I'm searching a solution without succes :confused: 

have you got en idea to help me ?

thank's a lot !

---

