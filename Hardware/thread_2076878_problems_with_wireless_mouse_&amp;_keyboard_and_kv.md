---
title: "problems with wireless mouse &amp; keyboard and kvm"
date: 2012-10-27
forum: Hardware
---

### Post by chris954 on 2012-10-27
I am running Ubuntu 12.04

1:
a) My configuration is that I have a 4 port KVM (ATEN) switch with 2 usb ports to a single monitor Requires keyboard in usb port for swtching (
b) I also have a 2nd 2 port kvm (Belkin) switch with 2 usb ports has it's own switch

2:
I want to use a wireless mouse & keyboard instead of a wired mouse & keyboard. I have used the following combination with the results as indicated. As a necessity I have to use kvm (a) to utilise all 4 ports.

W1) Using a Windows wireless keyboard and mouse in KVM (a) Ubuntu recognizes the Keyboard but not the mouse.

W2) Using a Logitech Wireless Keyboard & Mouse (MK855) in KVM (a) Ubuntu does not recognize either keyboard or mouse.

Both keyboards and mice are recognised if the the usb hub are plugged directly into the PC.
[SIZE=1][SIZE=2]Results of lsusb if (for this result i have plugged the Logitech usb into the pc and the MS usb into the KVM)[/SIZE][I]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 003 Device 003: ID 0424:2524 Standard Microsystems Corp. USB MultiSwitch Hub
Bus 001 Device 003: ID 0557:8021 ATEN International Co., Ltd 
[COLOR=Magenta]Bus 002 Device 006: ID 046d:c52b Logitech, Inc. Unifying Receiver[/COLOR]
Bus 002 Device 004: ID 05e3:0716 Genesys Logic, Inc. USB 2.0 Multislot Card Reader/Writer
Bus 003 Device 004: ID 04da:3903 Panasonic (Matsushita) 
Bus 003 Device 005: ID 04da:3903 Panasonic (Matsushita) 
Bus 003 Device 006: ID 050d:3201 Belkin Components F1DF102U/F1DG102U Flip KVM
Bus 001 Device 004: ID 0557:2213 ATEN International Co., Ltd CS682 2-Port USB 2.0 DVI KVM Switch[/I][/SIZE]

[SIZE=1][SIZE=2]Results of lsusb if (for this result i have plugged the Logitech usb into the KVM and the MS usb into the pc)[/SIZE][/SIZE]
root@ubuntu:/home/chris# lsusb
[SIZE=1][I]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 003 Device 003: ID 0424:2524 Standard Microsystems Corp. USB MultiSwitch Hub
Bus 001 Device 003: ID 0557:8021 ATEN International Co., Ltd 
[COLOR=Magenta]Bus 002 Device 007: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth[/COLOR]
Bus 002 Device 004: ID 05e3:0716 Genesys Logic, Inc. USB 2.0 Multislot Card Reader/Writer
Bus 003 Device 004: ID 04da:3903 Panasonic (Matsushita) 
Bus 003 Device 005: ID 04da:3903 Panasonic (Matsushita) 
Bus 003 Device 006: ID 050d:3201 Belkin Components F1DF102U/F1DG102U Flip KVM
Bus 001 Device 004: ID 0557:2213 ATEN International Co., Ltd CS682 2-Port USB 2.0 DVI KVM Switch[/I][/SIZE]

The items highlighted are the major 2 differences

Thank you for your support.

---

### Post by NetGO on 2012-10-28
I had similiar problem. 

In my case, if I turn on Opteron powernow feature in BIOS, Mouse and Keyboard works strange with my Belkin KVM.

Try turn off power management in BIOS and test it again. And in case of KVM, actually Highspeed USB setting in BIOS make response from keyboard and mouse slower. You can turn off highspeed setting in USB and can test as well. If you dont have any plan to attach USB 2.0 devices, turn off high speed will help, I guess.

I dont know why though.

---

### Post by NetGO on 2012-10-28
One more thing,

BIOS sometimes has handoff EHCI under usb. Try this with on and off.

---

