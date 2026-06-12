---
title: "Keyboard favorites multimedia keys not recognized"
date: 2010-08-18
forum: Hardware
---

### Post by 3esmit on 2010-08-18
Hello,

I brought a Microsoft Wireless Confort Desktop 5000, which comes with mouse and keyboard. The keyboard is named Microsoft Wireless Confort Keyboard 5000. 

There are like 20 multimedia keys:
Home,Mail,Documents,Media,**_Fav1_**,**_Fav2_**,**_Fav3_**,**_Fav4_**,**_Fav5_**,Favorites,*_ZoomOut_*,*_ZoomIn_*,Play/Pause,Prev Song, Next Song, Headphones, Mute, Volume -, Volume +, Calculator .

Additionally there is a strange key with that _Aero_ window switch symbol, that also are not recognized, that should act like one Super+Tab. And Also a Lock Key that have a lot of more things, but almost all work. Are: Help, Undo, Redo, New, Open, CLose, Reply, Forward, Send, *_SpellCheck, _*Save and Print

The problem is that I cannot use 9 multimedia keys (the underlined ones).

I have 3 /dev/input/event from this device, that are:
/dev/input/event5 (Keyboard) 
/dev/input/event6 (Mouse)
/dev/input/event7 (Multimedia Keyboard)
All are named "Microsoft Microsoft® 2.4GHz Transceiver v6.0"

The Fav1,Fav2,Fav3,Fav4,Fav5,Aero dosent even give some output when watching any of event (I expacted it in event7), all other multimedia give some crappy text when cat'in event7. ZoomIn (usb code 0xc022d) and ZoomOut (usb code 0xc022e) and SpellCheck give results, but need to be properly configured to be identified by XServer.

What I really cannot do is make kernel (or what manages it) found out that that Fav keys exists, or... well, I really have no idea why it dont give a signal of press, is like Im not pressing a thing.

lsusb:
```
Bus 004 Device 007: ID 045e:0745 Microsoft Corp. 
```dmesg:
```

[21586.796028] usb 4-2: new full speed USB device using uhci_hcd and address 9
[21586.970129] usb 4-2: configuration #1 chosen from 1 choice
[21586.978802] input: Microsoft Microsoft® 2.4GHz Transceiver v6.0 as  /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input23
[21586.978941] generic-usb 0003:045E:0745.0013: input,hidraw0: USB HID  v1.11 Keyboard [Microsoft Microsoft® 2.4GHz Transceiver v6.0] on  usb-0000:00:1d.2-2/input0
[21586.985807] input: Microsoft Microsoft® 2.4GHz Transceiver v6.0 as  /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.1/input/input24
[21586.985940] generic-usb 0003:045E:0745.0014: input,hidraw1: USB HID  v1.11 Mouse [Microsoft Microsoft® 2.4GHz Transceiver v6.0] on  usb-0000:00:1d.2-2/input1
[21587.011325] input: Microsoft Microsoft® 2.4GHz Transceiver v6.0 as  /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.2/input/input25
[21587.011547] generic-usb 0003:045E:0745.0015: input,hiddev96,hidraw2:  USB HID v1.11 Device [Microsoft Microsoft® 2.4GHz Transceiver v6.0] on  usb-0000:00:1d.2-2/input2
```Thank you for the attention!

---

