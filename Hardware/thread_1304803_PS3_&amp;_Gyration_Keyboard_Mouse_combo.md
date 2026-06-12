---
title: "PS3 &amp; Gyration Keyboard Mouse combo"
date: 2009-10-29
forum: Hardware
---

### Post by Pickled Onion on 2009-10-29
I'm a complete noob when it comes to Linux and just thought i'd give it a whirl on my lovely little ps3 - please be gentle.
 
Had a few installation problems but resolved them (speed of CD burn of the ubuntu image etc..) 
 
I'm now faced with an issue with my Gyration Keyboard and Mouse. Basically the mouse works but the keyboard doesn't.
 
Its a GC15 Go Pro that works fine on everything else (including the PS Gameos) but not in Ubuntu 9.04.
 
It looks like the the RF Receiver is picked up correctly as Ive had a look in Dev/input/by id and can see:
usb-Apple__Inc_Apple_Keyboard-event-kbd
usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd
usb-Gyration_Gyration_RF_Technology_Receiver-event-mouse
usb-Gyration_Gyration_RF_Technology_Receiver-mouse
 
Which is spot on as I have an Wired Apple keyboard [using this until i can get the keyboard working properly] and the Gyration USB RF Stick also plugged in.
 
What im unsure of is the obvious - why the keyboard isn't working properly and why there would be 2 references (above) to a mouse and 1 for a keyboard.
 
Also i've had a look at a couple of logs:
 
Oct 29 15:50:20 ubuntu kernel: [ 2456.647429] usb 1-2.2: new low speed USB device using ps3-ehci-driver and address 6
Oct 29 15:50:21 ubuntu kernel: [ 2456.745383] usb 1-2.2: configuration #1 chosen from 1 choice
Oct 29 15:50:21 ubuntu kernel: [ 2456.754764] input: Gyration Gyration RF Technology Receiver as /devices/ps3_system/sb_05/usb1/1-2/1-2.2/1-2.2:1.0/input/input5
Oct 29 15:50:21 ubuntu kernel: [ 2456.779577] gyration 0003:0C16:0002.0005: input,hiddev96,hidraw2: USB HID v1.10 Keyboard [Gyration Gyration RF Technology Receiver] on usb-sb_05-2.2/input0
Oct 29 15:50:21 ubuntu kernel: [ 2456.787477] input: Gyration Gyration RF Technology Receiver as /devices/ps3_system/sb_05/usb1/1-2/1-2.2/1-2.2:1.1/input/input6
Oct 29 15:50:21 ubuntu kernel: [ 2456.839378] gyration 0003:0C16:0002.0006: input,hiddev97,hidraw3: USB HID v1.20 Mouse [Gyration Gyration RF Technology Receiver] on usb-sb_05-2.2/input1
 
some more info from xorg.log
II) config/hal: Adding input device Gyration Gyration RF Technology Receiver
(II) Synaptics touchpad driver version 0.99
 
So it does look as if it is seeing the two events off RF USB reciever but using the incorrect driver in Linux (The touchpad).
 
The Touchpad element would hold as I under one of the mouse configuration items there is a radio box for a Touchpad.. Untick the box and the mouse stops functioning.
 
So... how do i change this and where can i get the correct driver from?
 
 
HELP !

---

