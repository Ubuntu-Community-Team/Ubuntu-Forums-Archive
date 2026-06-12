---
title: "Bluetooth stopped working"
date: 2009-05-20
forum: Hardware
---

### Post by DoctorT on 2009-05-20
I'm running Ubuntu 9.04 (Jaunty Jackalope) on my HP laptop, and I have been using a USB Bluetooth adapter for my mouse and keyboard, and they had been working just fine. But recently, they stopped working alltogether. It's driving me crazy, because I've been stuck using my crappy notepad "mouse". I've searched for similar problems, but none of the solutions I have found helped me. 

So here's how it happened: 

Back when my bluetooth was working, it would only work after I unplugged the adapter and replugged it in. The strange thing was that it showed the bluetooth icon at first (before I unplugged the adapter, when it didn't work), but then after I replugged the adapter in, the icon was missing (I have the Bluetooth Preference set to "only display when adapter present"), but my mouse and keyboard would then work. 

This led me to believe that the default gnome bluetooth system was interfering with whatever application was actually making the bluetooth work, so I removed the bluetooth application from the Startup list, to see if it would allow my bluetooth to work without having to replug the adapter in every time I started my computer. But after that (I believe, I'm not positive it was because of that... this was about the same time I upgraded to Jaunty), my bluetooth stopped working. 

Even after attempting to add the bluetooth app back to the Startup list (I copied the command from my friend's computer, same version of Ubuntu and stuff, to be safe... I think it was "bluetooth-applet"), it still wouldn't work. I've since then tried to uninstall all the bluetooth and bluez packages from Synaptic (except libbluetooth3... it was prompting to uninstall a lot of other things), and reinstall them, but to no avail. 

I then went in search of help from the web. I found a variety of other threads about similar problems, but none of them have helped at all. Here's some information about the things I've tried, to save time: 

```
$ sudo modprobe btusb
$ dmesg | tail
[  319.772156] hub 4-1:1.0: USB hub found
[  319.775983] hub 4-1:1.0: 3 ports detected
[  320.057576] usb 4-1.2: new full speed USB device using uhci_hcd and address 10
[  320.209826] usb 4-1.2: configuration #1 chosen from 1 choice
[  320.221182] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1.2/4-1.2:1.0/input/input16
[  320.252700] generic-usb 0003:046D:C71B.0005: input,hidraw0: USB HID v1.11 Keyboard [Logitech Logitech BT Mini-Receiver] on usb-0000:00:1a.1-1.2/input0
[  320.330496] usb 4-1.3: new full speed USB device using uhci_hcd and address 11
[  320.496537] usb 4-1.3: configuration #1 chosen from 1 choice
[  320.512533] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1.3/4-1.3:1.0/input/input17
[  320.524094] generic-usb 0003:046D:C71C.0006: input,hiddev96,hidraw1: USB HID v1.11 Mouse [Logitech Logitech BT Mini-Receiver] on usb-0000:00:1a.1-1.3/input0
```

```
$ hcitool dev
Devices:
$ 
```
As you can see, there's no devices found. 

If anyone has some ideas or suggestions as to what might be the problem, or what I can try, I would be much appreciative.

---

### Post by DoctorT on 2009-05-20
Bump... :-(

---

### Post by tiki pirate on 2009-06-22
Found this thread when I had a similar problem with 9.04 and my Logitech bluetooth mouse.

Worked fine one day.  Next day it would not work.  When I went to add new device or try to reconnect with would fail.

My solution was to right click the bluetooth icon > prefrences .. then deleted my mouse as a known device (it was showing up even when turned off). 

 I was then able to go back to"add new device" added it, and have it work fine.

It seemed to reset the whole thing.  I hope this helps somebody out.

---

