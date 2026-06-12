---
title: "USB mouse becomes slow and jerky - help needed!"
date: 2017-05-20
forum: Hardware
---

### Post by chrisonbuntu on 2017-05-20
I have a DELL Latitude laptop running 17.04 Ubuntu Gnome and I am struggling with a USB logitech mouse.

Most of the time the mouse is great, smooth, responsive and accurate.  BUT, sometimes when waking from sleep the mouse pointer starts moving slowly and intermittently.  This makes is practically impossible to use.  

In-built trackpad keeps running fine.
The problem exists at the login screen and when logged in as different users.  Unplugging the USB dongle and re-plugging doesnt solve it, nor does playing with the mouse settings (speed etc).

I have run some USB and dmesg commands in the terminal, but cant see anything obviously wrong.  Please help!!

```
run dmesg, there are three lines relating to logitech mouse.  top is when it worked, lower is after bug appeared:

input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/0003:046D:C51B.0001/input/input8
input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/0003:046D:C51B.0003/input/input18

hid-generic 0003:046D:C51B.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1.3/input0
hid-generic 0003:046D:C51B.0003: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1.3/input0

hid-generic 0003:046D:C51B.0002: hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-1.3/input1
hid-generic 0003:046D:C51B.0004: hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-1.3/input1
----------------

$ lsusb

Bus 002 Device 004: ID 0a5c:5800 Broadcom Corp. BCM5880 Secure Applications Processor
Bus 002 Device 006: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0461:4db1 Primax Electronics, Ltd 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


$ sudo grep -B3 -A6 046d.*c51b /sys/kernel/debug/usb/devices
[sudo] password for chris: 

T:  Bus=02 Lev=02 Prnt=02 Port=02 Cnt=01 Dev#=  6 Spd=1.5  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c51b Rev=46.00
S:  Manufacturer=Logitech
S:  Product=USB Receiver
C:* #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr= 98mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:* If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid

(this shows a polling interval of 10ms and speed of 1.5 - both appear OK)


```

---

### Post by chrisonbuntu on 2017-06-21
4 weeks and noone has even read this post.  Is this not the place to put questions?

---

### Post by him610 on 2017-06-22
Hello chrisonbuntu,

If no answer received within 12 hours, feel free to 'bump'. Sometimes a post will fall to the bottom of the heap and get overlooked by the moderators. 

That said, I don't believe I can offer any advice with your mouse issue other than try another mouse if you have one. Computer mice do go bad on occasion, but your issue sounds like all processes are not waking completely after sleep/suspend, or a memory leak. 

The newer Logitech cordless mouse models use what is called a Logitech Unifying Receiver to communicate with the mouse. I have three M325 mice I use on different computers, plus another paired with a K400r keyboard that I use occasionally. Never had a problem with any of them. I have had wired mice behave erratically though resulting in R&R (Remove and Replace.)

> sometimes when waking from sleep the mouse pointer starts moving slowly and intermittently

How does the mouse behave after a system reboot?

---

