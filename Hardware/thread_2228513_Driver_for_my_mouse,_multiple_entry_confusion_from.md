---
title: "Driver for my mouse, multiple entry confusion from lsusb and simular"
date: 2014-06-07
forum: Hardware
---

### Post by michael171 on 2014-06-07
I was hoping someone from the ubuntu community could provide me some insight into identifying what driver my mouse is using.  I have used lsusb, xinput alongside dumping kern.log and dmesg | egrep Logitech.  It apears that my mouse uses multiple drivers as evedent by the two ids listed from xinput and the multiple entrys of dmesg pertaining to Logitech.  I cannot figure out what driver is doing the pointer and what one is doing the keyboard (my mouse has a keyboard).

Here are some parsed outputs I have aquired

```
xinput -list | egrep Logitech > ./Documents/xinput-Logitech
```
> &#9116;   &#8627; Logitech Gaming Mouse G600                  id=8    [slave  pointer  (2)]
&#9116;   &#8627; Logitech Gaming Mouse G600                  id=9    [slave  pointer  (2)]
&#9116;   &#8627; Logitech Logitech Illuminated Keyboard      id=11    [slave  pointer  (2)]
    &#8627; Logitech Logitech Illuminated Keyboard      id=10    [slave  keyboard (3)]

```
cat /var/log/kern.log | egrep Logitech > ./Documents/kernlog-Logitech.txt
```
> Jun  6 00:32:47 bb kernel: [    1.742584] usb 3-2: Manufacturer: Logitech
Jun  6 00:32:47 bb kernel: [    1.770924] input: Logitech Gaming Mouse G600 as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input5
Jun  6 00:32:47 bb kernel: [    1.771097] hid-generic 0003:046D:C24A.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech Gaming Mouse G600] on usb-0000:00:1a.0-2/input0
Jun  6 00:32:47 bb kernel: [    1.794671] input: Logitech Gaming Mouse G600 as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.1/input/input6
Jun  6 00:32:47 bb kernel: [    1.794801] hid-generic 0003:046D:C24A.0002: input,hiddev0,hidraw1: USB HID v1.11 Keyboard [Logitech Gaming Mouse G600] on usb-0000:00:1a.0-2/input1
Jun  6 00:32:47 bb kernel: [    3.169937] usb 4-1: Product: Logitech Illuminated Keyboard
Jun  6 00:32:47 bb kernel: [    3.169940] usb 4-1: Manufacturer: Logitech
Jun  6 00:32:47 bb kernel: [    3.178388] input: Logitech Logitech Illuminated Keyboard as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input7
Jun  6 00:32:47 bb kernel: [    3.178532] hid-generic 0003:046D:C318.0003: input,hidraw2: USB HID v1.11 Keyboard [Logitech Logitech Illuminated Keyboard] on usb-0000:00:1a.1-1/input0
Jun  6 00:32:47 bb kernel: [    3.182038] input: Logitech Logitech Illuminated Keyboard as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.1/input/input8
Jun  6 00:32:47 bb kernel: [    3.182171] hid-generic 0003:046D:C318.0004: input,hiddev0,hidraw3: USB HID v1.11 Device [Logitech Logitech Illuminated Keyboard] on usb-0000:00:1a.1-1/input1
Jun  6 16:28:57 bb kernel: [    1.750589] usb 3-2: Manufacturer: Logitech
Jun  6 16:28:57 bb kernel: [    1.778965] input: Logitech Gaming Mouse G600 as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input5
Jun  6 16:28:57 bb kernel: [    1.779072] hid-generic 0003:046D:C24A.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech Gaming Mouse G600] on usb-0000:00:1a.0-2/input0
Jun  6 16:28:57 bb kernel: [    1.802690] input: Logitech Gaming Mouse G600 as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.1/input/input6
Jun  6 16:28:57 bb kernel: [    1.802889] hid-generic 0003:046D:C24A.0002: input,hiddev0,hidraw1: USB HID v1.11 Keyboard [Logitech Gaming Mouse G600] on usb-0000:00:1a.0-2/input1
Jun  6 16:28:57 bb kernel: [    3.178939] usb 4-1: Product: Logitech Illuminated Keyboard
Jun  6 16:28:57 bb kernel: [    3.178942] usb 4-1: Manufacturer: Logitech
Jun  6 16:28:57 bb kernel: [    3.187384] input: Logitech Logitech Illuminated Keyboard as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input7
Jun  6 16:28:57 bb kernel: [    3.187519] hid-generic 0003:046D:C318.0003: input,hidraw2: USB HID v1.11 Keyboard [Logitech Logitech Illuminated Keyboard] on usb-0000:00:1a.1-1/input0
Jun  6 16:28:57 bb kernel: [    3.191026] input: Logitech Logitech Illuminated Keyboard as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.1/input/input8
Jun  6 16:28:57 bb kernel: [    3.191171] hid-generic 0003:046D:C318.0004: input,hiddev0,hidraw3: USB HID v1.11 Device [Logitech Logitech Illuminated Keyboard] on usb-0000:00:1a.1-1/input1

From this I cannot determine weather the pointer is input0, input1 or even input5.  And what driver is handling the keyboard part.  I need this device driver name so that I can make a custom xorg.conf for this mouse and eventualy a python3 script that will help users with this mouse.

Using Ubuntu 14

---

### Post by papibe on 2014-06-07
Hi michael171. Welcome to the forum ):P

You should be able to see if a device is active, or enable, by running this for the mouse:
```
xinput list-props 8

xinput list-props 9
```
For each command, the second line of the output should tell you if the device is active or not. The last one shows which device it is.

Hope it helps. Let us know how it goes.

Come here often and have fun.
Regards.

---

### Post by michael171 on 2014-06-08
Thank you paplibe, this was very helpfull, it shows them both as being enabled but what I learned is that evdev is the driver that my mouse is using.  Thank you, I greatly apreciate the welcome.  I have after some research determined that modifying the xorg.conf would only create a static mapping that ocures each time the x server is started but that instead if I use xlib module that was ported to python3 I can hook (or rather grab the keypad) via the x server protocol of my mouse which i have identifyed as having the handler sysrq kbd event3.  I found a utility which did actualy alow me to map a button to gedit , the program is called actkbd and there was no debian or ubuntu packages available so I downloaded and compiled, which was very easy and it works.  I am actualy looking into making eventualy a full gui application that mimmics that of the windows logitech gaming software for this mouse.  When I have a working product I would share the source code with the community.  

Thank you.

---

