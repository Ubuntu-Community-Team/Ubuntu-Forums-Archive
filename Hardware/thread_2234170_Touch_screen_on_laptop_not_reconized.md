---
title: "Touch screen on laptop not reconized"
date: 2014-07-13
forum: Hardware
---

### Post by russ9 on 2014-07-13
Dell inspiron inspiron 15-3521
Intel core I3

new laptop not that old or I would presume. Touch screen worked great while using windows 8.1 but not even recognized as a touch screen in ubuntu 14.? Newest version....

Installed runtime configuration and test of xinput devices. When I run the test no touch screen devices are found...

It is an Elan Microelectronics touch screen this I found pated below. But can not find driver for Elan 04f3:0042 screen nor get ubuntu to recognize it even as a touch screen. 

Been fighting this thing for a couple days now and no luck yet. Cant remember the other packages I install trying but failing to get it to work. 

russ@russ-Inspiron-3521:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0a5c:21d7 Broadcom Corp. 
Bus 001 Device 004: ID 04f3:0042 Elan Microelectronics Corp. 
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 006: ID 064e:812e Suyin Corp.

---

### Post by Vladlenin5000 on 2014-07-13
Hi, welcome.

Your touchpad is natively supported and Ubuntu certified, no less...
Please make sure it isn't turned off (BIOS and/or keyboard switch/FN key combo).

---

### Post by russ9 on 2014-07-13
Cant find a setting in ubuntu or my bios to turn on or eneable touchpad. Fn+f1 which is my screen key only put numbers over my icons in my tray and isnt turning the touch screen on or off neither.  
Found another thread to turn it on using terminal. 

xinput &#8211;enable &#8220;Elan&#8221; and this is what I get.

russ@russ-Inspiron-3521:~$ xinput &#8211;enable &#8220;elan&#8221;
usage :
    xinput get-feedbacks <device name>
    xinput set-ptr-feedback <device name> <threshold> <num> <denom>
    xinput set-integer-feedback <device name> <feedback id> <value>
    xinput get-button-map <device name>
    xinput set-button-map <device name> <map button 1> [<map button 2> [...]]
    xinput set-pointer <device name> [<x index> <y index>]
    xinput set-mode <device name> ABSOLUTE|RELATIVE
    xinput list [--short || --long || --name-only || --id-only] [<device name>...]
    xinput query-state <device name>
    xinput test [-proximity] <device name>
    xinput create-master <id> [<sendCore (dflt:1)>] [<enable (dflt:1)>]
    xinput remove-master <id> [Floating|AttachToMaster (dflt:Floating)] [<returnPointer>] [<returnKeyboard>]
    xinput reattach <id> <master>
    xinput float <id>
    xinput set-cp <window> <device>
    xinput test-xi2 <device>
    xinput map-to-crtc <device> <crtc name>
    xinput list-props <device> [<device> ...]
    xinput set-int-prop <device> <property> <format (8, 16, 32)> <val> [<val> ...]
    xinput set-float-prop <device> <property> <val> [<val> ...]
    xinput set-atom-prop <device> <property> <val> [<val> ...]
    xinput watch-props <device>
    xinput delete-prop <device> <property>
    xinput set-prop <device> [--type=atom|float|int] [--format=8|16|32] <property> <val> [<val> ...]

Still nothing even after reboot. Cant touch my screen and make anything happen.
Still no calibratable devices found when I try to calibrate.

---

### Post by Vladlenin5000 on 2014-07-13
Quoting myself:

> **Vladlenin5000 said:**
> Please make sure it isn't turned off (BIOS _and_/_or_ _**keyboard switch/FN key combo**_).

---

### Post by russ9 on 2014-07-13
No keyboard switch. No option in bios to turn off or on for the touch screen, matter of fact everything in bios enabled excluding usbd debugging. No switch noticable, have hit fn+all keys on keyboard. No switch or option in settings. No other forum post is working for me neither. 

So please stop with keyboard switch and bios tips. Give me something new I have not tried already..........

---

### Post by Vladlenin5000 on 2014-07-13
> **russ9 said:**
> So please stop with keyboard switch and bios tips. Give me something new I have not tried already..........

Hummm... Do I have to? Are you paying for my time? I don't think so... And considering I have anything better to offer at the moment this is a good bye and good luck.

---

### Post by russ9 on 2014-07-14
I appreciate your help as it did lead me to finding and trying new things, but what you keep saying I have already looked, investigated with attepmts to use keyboard controls and bios settings to turn on the touch screen. I am boggled much this as ubuntu did say my laptop is ubuntu certified. But for some unknown reason I cant get this feature to work with ubuntu.

---

