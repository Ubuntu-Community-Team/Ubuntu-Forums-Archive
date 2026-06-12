---
title: "Installation DVB-T U7200"
date: 2009-07-18
forum: Hardware
---

### Post by Cisbot on 2009-07-18
Hello, I'm a new user of ubuntu forum. I need help to install my DVD-T U7200 Gigabyte, in fact i can't find any type of driver that work properly. In Gigabyte's site there isn't the linux driver  for my device...

searching on internet, someone suggest me to type in terminal "lsusb" with the usb card connected.
The response is the follow:

Bus 005 Device 002: ID 1044:7005 Chu Yuen Enterprise Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

Can anyone help me to configure it?
thanks!:)

---

### Post by Cisbot on 2009-07-20
Hello?? help!!:)

---

### Post by glenkelp on 2009-07-29
I have exactly same problem. I would like to get my Gigabyte GT-U7200 USB DVB-T working on Ubuntu 9.04.
I followed some instructions on [https://help.ubuntu.com/community/DVB-T_(USB](https://help.ubuntu.com/community/DVB-T_(USB)) and tried to get some help from linuxtv.org wikipages, but as this device was not listed anywhere, I could not find a working way to get my device connected.
I is worth mentioning that I'm rather new to linux and don't understand the inner parts of it very well, but getting my hands dirty is no problem.
I couldn't get this device correctly working on WinXP either, but I was really hoping Ubuntu and linux will do the trick. Too bad it's not supported natively. Maybe someone is even using this device on linux?

It's kind of confusing and I don't have an idea how to get this working. Thanks for help!

---

### Post by glennodotcom on 2009-09-12
Like the previous posters, I cannot get it to work either. Steps I have taken are:

Tried Jaunty and Karmic Alpha5 64bit builds to see if either work - no joy
Compiled and installed Video for Linux modules - no joy
Added the vendor ID to the USBHID quirks parameter to ensure the ir interface doesn't get bound to another driver - no joy
Translated an Italian posting that the tuner uses a Afatech 9035-N2 chipset - the Italians had no joy getting it to work either!

lspci reveals:
Bus 001 Device 011: ID 1044:7005 Chu Yuen Enterprise Co., Ltd

var/message revels on insert:
input: GIGABYTE Technologies Inc. U7200 USB TV Device as /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.1/input/input8
generic-usb 0003:1044:7005.0005: input,hidraw4: USB HID v1.01 Keyboard [GIGABYTE Technologies Inc. U7200 USB TV Device] on usb-0000:00:1a.7-4/input1

I do not think there is an easy path to making this device work - without cutting some code (which I do not have the skills to do)!

---

### Post by Scaramunga on 2010-02-04
Sorry to bump an old topic, but has anyone managed to get this tuner card working yet?

---

### Post by Rdrick on 2010-07-03
Hi people, 

I am having the same problem (on linuxtv.org wiki still listed as unsupported) and it seems this is the only topic  mentioning my TV tuner, so I am asking the stupid question once more, do  you have solution anybody?

hope someone helps me...

---

### Post by glenkelp on 2010-08-17
After having this device for long time now, I haven't managed to get it working in Ubuntu (now 10.04). Does anyone know something about dealing with DVB-T USB tuners, or can anyone point out where to post, to get someone skilled and involved to work on including support on this Gigabyte GT-U7200. It's rather annoying to boot to Win every time I want to watch TV on my computer and I really hate win by now.
Sorry, that didn't help any previous poster, but I see the problem is still up.

Help!

---

