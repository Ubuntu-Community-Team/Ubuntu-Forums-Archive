---
title: "zx-6000 Headset"
date: 2009-02-17
forum: Hardware
---

### Post by Sojurner on 2009-02-17
I have the Microsoft zx-6000 wireless usb headset. Since microsoft only makes drivers for their operating systems does anyone here have any idea how i can make this work.

Its a usb headset that is wireless. (ie the tx/rx portion plugs in via usb, and the headset itself is wireless)

Its basically useless right now and i would love to get it working if at all possible.

---

### Post by albandy on 2009-02-17
do this in console:
tail -f /var/log/messages

plug the headset and type the messages 

I'm using a plantronics wireless headset and works perfect

---

### Post by Sojurner on 2009-02-17
could u explain a little further

Exactly what messages am i supposed to type? When i plugged it in i saw that it detected the Xbox360 Wireless Reciever but it not working yet.

I see where it made it imput 12, 13, 14 and 15. but im confused as to what to do next.

This is what it says

 Feb 17 10:05:11 sojurner-desktop kernel: [91925.628025] usb 1-2: new full speed USB device using ohci_hcd and address 10
Feb 17 10:05:11 sojurner-desktop kernel: [91925.855545] usb 1-2: configuration #1 chosen from 1 choice
Feb 17 10:05:11 sojurner-desktop kernel: [91925.865489] input: Xbox 360 Wireless Receiver as /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.0/input/input12
Feb 17 10:05:11 sojurner-desktop kernel: [91925.933447] input: Xbox 360 Wireless Receiver as /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.2/input/input13
Feb 17 10:05:11 sojurner-desktop kernel: [91925.993871] input: Xbox 360 Wireless Receiver as /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.4/input/input14
Feb 17 10:05:11 sojurner-desktop kernel: [91926.081751] input: Xbox 360 Wireless Receiver as /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.6/input/input15

---

### Post by albandy on 2009-02-17
1.- Open a gnome-terminal
2.- type tail -f /var/log/messages
3.- Plug your usb adapter in the usb socket of your computer
4.- Some messages will appear in the gnome-terminal, copy it and paste it here

---

### Post by Sojurner on 2009-02-17
yea it took me a second to realize what you ment.. i posted them above

---

### Post by Sojurner on 2009-02-17
This is what it says

 Feb 17 10:05:11 sojurner-desktop kernel: [91925.628025] usb 1-2: new full speed USB device using ohci_hcd and address 10
Feb 17 10:05:11 sojurner-desktop kernel: [91925.855545] usb 1-2: configuration #1 chosen from 1 choice
Feb 17 10:05:11 sojurner-desktop kernel: [91925.865489] input: Xbox 360 Wireless Receiver as /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.0/input/input12
Feb 17 10:05:11 sojurner-desktop kernel: [91925.933447] input: Xbox 360 Wireless Receiver as /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.2/input/input13
Feb 17 10:05:11 sojurner-desktop kernel: [91925.993871] input: Xbox 360 Wireless Receiver as /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.4/input/input14
Feb 17 10:05:11 sojurner-desktop kernel: [91926.081751] input: Xbox 360 Wireless Receiver as /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.6/input/input15

---

### Post by albandy on 2009-02-17
By the moment it's not supported, but it will be.

My USB Wireless headset it's recognized directly as a soundcard.

I've been reading about zx-6000, it uses the XBOX receiver, so maybe this will help you

[http://ubuntuforums.org/showpost.php?p=2512158](http://ubuntuforums.org/showpost.php?p=2512158)
[http://ubuntuforums.org/showthread.php?t=318382&highlight=xbox+360+edgy](http://ubuntuforums.org/showthread.php?t=318382&highlight=xbox+360+edgy)

---

### Post by kostkon on 2009-02-17
Could you please connect the headset and then in a terminal give
```
aplay -l
```
and check if the output shows the headset. Also, post the output of this command here, if you want.

---

### Post by Acuity101 on 2009-06-27
Not that this might be useful, but same here as Sojurner.

Tailing messages gives:
[FONT=monospace]Jun 27 05:54:06 ubuntu kernel: [ 4026.560050] usb 3-1: new full speed USB device using uhci_hcd and address 5
Jun 27 05:54:06 ubuntu kernel: [ 4026.835885] usb 3-1: configuration #1 chosen from 1 choice
Jun 27 05:54:06 ubuntu kernel: [ 4026.838295] input: Xbox 360 Wireless Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input24
Jun 27 05:54:06 ubuntu kernel: [ 4026.906420] input: Xbox 360 Wireless Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.2/input/input25
Jun 27 05:54:06 ubuntu kernel: [ 4026.970237] input: Xbox 360 Wireless Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.4/input/input26
Jun 27 05:54:07 ubuntu kernel: [ 4027.030703] input: Xbox 360 Wireless Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.6/input/input27

And list of playback devices command gives:
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC260 Analog [ALC260 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[/FONT]

---

