---
title: "How to find Keyboard/ Mouse Serial number or information"
date: 2013-03-04
forum: Hardware
---

### Post by venkia9 on 2013-03-04
Hi,

How to find Keyboard/Mice serial number or information through terminal. 
I want to capture 200 machiens mice and keyboard information, if i get this information through terminal its really help for me.

Thank you
Venkat

---

### Post by gordintoronto on 2013-03-04
This is from a source who should know: "keyboards do not, as a rule, communicate about what they are to the computer." Mice are even worse.

---

### Post by venkia9 on 2013-03-08
Hi,

My aim is to identify how many mice/keyboard connected to remote machiens. I need to catpure huge amount of machines. 

when i open /dev/input/by-path  I am getting below output 

[COLOR=#222222][FONT=arial]/dev/input/by-path$ ls

pci-0000:00:14.0-usb-0:2:1.0-event-mouse
pci-0000:00:14.0-usb-0:2:1.0-mouse
pci-0000:00:14.0-usb-0:4.4:1.0-event-kbd
pci-0000:00:14.0-usb-0:4.4:1.1-event-mouse
pci-0000:00:14.0-usb-0:4.4:1.1-mouse

[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]

Here i connected one mice and keyboard can you please explain why mice appear as 4 times keyboard as 1 time

when i connect extra mice i get below output
[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]
[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]/dev/input/by-path$ ls

pci-0000:00:14.0-usb-0:2:1.0-event-mouse

pci-0000:00:14.0-usb-0:2:1.0-mouse

pci-0000:00:14.0-usb-0:4.1:1.0-event-mouse

pci-0000:00:14.0-usb-0:4.1:1.0-mouse

pci-0000:00:14.0-usb-0:4.4:1.0-event-kbd

pci-0000:00:14.0-usb-0:4.4:1.1-event-mouse

pci-0000:00:14.0-usb-0:4.4:1.1-mouse

[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]
[/FONT][/COLOR]

when i connect my OTP device its showing as 
[COLOR=#222222][FONT=arial]pci-0000:00:14.0-usb-0:2:1.0-event-mouse[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]pci-0000:00:14.0-usb-0:2:1.0-mouse[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]pci-0000:00:14.0-usb-0:4.1:1.0-event-kbd[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]pci-0000:00:14.0-usb-0:4.4:1.0-event-kbd[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]pci-0000:00:14.0-usb-0:4.4:1.1-event-mouse[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]pci-0000:00:14.0-usb-0:4.4:1.1-mouse


[/FONT][/COLOR]

---

