---
title: "Slow USB mouse (and USB everything I think)"
date: 2009-05-13
forum: Hardware
---

### Post by merj on 2009-05-13
Hi

A bit of a long story because I want to give you all the information:

I started off trying to install my new webcam on my laptop and downloaded EasyCam2 as was suggested on some Ubuntu documentation. (While I was installing it with synaptic I realised I was installing both the gnome and kde versions so cancelled and resstarted it - but I don't know if that's relevant).

Before even getting to see if it could do anything for the webcam, my mouse stopped working properly: the wireless mouse/keyboard and wired mouse are very slow/unresponisve and jump, as though it is taking to long for the signal to get to  the computer. The laptops own keyboard and touchpad do still work so I think the problem is with the USB.

So the things I've tried:
1) Complete removal of Easycam2.
2) removal of all the other bits that were installed with EasyCam2 (by looking in the history in synaptic).
3) Upgrading from Ubuntu 8.04 to 8.09 (which I'm on at the moment).
4) removing and restarting ehci_hcd and uhci_hcd with rmmod and modprobe (although couldn't rmmod uhci_hcd)

From searching other posts, info that may be helpful for solving this one:

lsusb
```
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0461:4d03 Primax Electronics, Ltd Kensington Mouse-in-a-box
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

dmesg | grep usb
```
 
[    3.164596] usbcore: registered new interface driver usbfs
[    3.164636] usbcore: registered new interface driver hub
[    3.172076] usbcore: registered new device driver usb
[    3.180840] usb usb1: configuration #1 chosen from 1 choice
[    3.388954] usb usb2: configuration #1 chosen from 1 choice
[    3.500092] usb 1-2: new low speed USB device using uhci_hcd and address 2
[    3.597016] usb usb3: configuration #1 chosen from 1 choice
[    3.816319] usb usb4: configuration #1 chosen from 1 choice
[    4.608044] usb 1-2: new low speed USB device using uhci_hcd and address 3
[    6.104323] usb 1-2: configuration #1 chosen from 1 choice
[   19.378752] usbcore: registered new interface driver hiddev
[   19.744658] input: HID 0461:4d03 as /devices/pci0000:00/0000:00:10.0/usb1/1-2/1-2:1.0/input/input8
[   19.772402] input,hidraw0: USB HID v1.00 Mouse [HID 0461:4d03] on usb-0000:00:10.0-2
[   19.772441] usbcore: registered new interface driver usbhid
[   19.772460] usbhid: v2.6:USB HID core driver

```

After unplugging and plugging the mouse in again, I need to run lsusb to get it to respond at all and then it detects nothing:
lsusb:
```
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

after this I get
```

:~$ dmesg |tail
[  659.248508] psmouse.c: TouchPad at isa0060/serio3/input0 lost sync at byte 1
[  659.250414] psmouse.c: TouchPad at isa0060/serio3/input0 lost sync at byte 1
[  659.252409] psmouse.c: TouchPad at isa0060/serio3/input0 lost sync at byte 1
[  659.260724] psmouse.c: TouchPad at isa0060/serio3/input0 lost sync at byte 1
[  659.260729] psmouse.c: issuing reconnect request
[ 1617.624088] usb 1-2: USB disconnect, address 3
[ 1625.768060] usb 1-2: new low speed USB device using uhci_hcd and address 4
[ 1627.320583] usb 1-2: configuration #1 chosen from 1 choice
[ 1628.048496] input: HID 0461:4d03 as /devices/pci0000:00/0000:00:10.0/usb1/1-2/1-2:1.0/input/input10
[ 1628.072327] input,hidraw0: USB HID v1.00 Mouse [HID 0461:4d03] on usb-0000:00:10.0-2

```

Oh, and sometimes the Device Manager says for this USB Device:
"Insufficient power to operate USB device."
- Could it be that plugging the webcam in "blew" the USB port? And actually it's a harware problem? Can that happen?

I would be very grateful for any suggestions.
Thanks

---

### Post by stretch427 on 2009-05-13
To me it looks like you have some USB 1.1 ports. And If you try and plug a USB 2.0 in there it could effect speed. It looks like you have one 2.0 port so try and determine which that one is. How old is your laptop? Because all newer laptops all have 2.0. That also might be the reason for the "not enough power" problem. I doubt your webcam blew anything.

---

### Post by merj on 2009-05-13
Thanks for the quick reply. It is an old laptop and actually I can only find 3 USB ports, I'm not too sure where this fourth USB 2.0 port is.

The thing is, up until 2 days ago the mouse and everything worked fine on the USB 1.0 ports. It's also an old mouse so I don't think that's the problem. Any other ideas? I don't know if I can reinstall USB drivers or something like that?

Glad to know it's unlikely that the webcam messed up anything serious.

---

### Post by stretch427 on 2009-05-13
Do you have a live cd? if so you could boot from that you could select fix broken packages. That might do it.  It could be that if you removed some of those packages, you could have removed some basic things on accident.  Let me know how that works.

---

### Post by merj on 2009-05-14
Thanks

I tried booting from the Live CD (Hardy Herron because that's what I have lying around). Even then I had the laggy mouse problem. Does that mean that it's something more fundamental than the OS? 

I'm not too sure about fixing broken packages. Both on my normal Ubuntu, and the live CD, Synaptic Package Manager says that there are 0 broken packages.

Thanks

---

### Post by stretch427 on 2009-05-14
When you try and drag a window what happens?

If it splits up and is really laggy it is graphics driver problems. And you might just have to deal with it until you can find and install the right drivers. Or maybe try using an onboard port rather than a graphics card,( if you have one).

that could have been caused by an upgrade. Breaking the drivers with a kernel update. 

See if its your GPU and let me know what you find out. 
Cheers!

---

### Post by merj on 2009-05-15
The window dragging is a little laggy, but not nearly as much as the mouse and I think may just be because of the old computer. Using the touchpad on the laptop produces no lag at all, so I don't think it's the graphics driver.

The only other things I upgraded at the time of the breakage was:
libpango1.0-0 (1.20.5-0ubuntu1) to 1.20.5-0ubuntu1.1
libpango1.0-common (1.20.5-0ubuntu1) to 1.20.5-0ubuntu1.1

upgrade to 8.10 came later.

How would I go about fixing drivers? I haven't been able to find anything on reinstalling them.

Thanks for all your help.

---

### Post by breephd on 2009-08-09
did you figure out how to fix, replace drivers?  i am not even sure how to install drivers.  i think i did it. but i'm not sure...

---

### Post by nutsy.ben on 2009-09-28
Hi Guys.

I have the same probleme on a HP pavilion m7265.
THe USB HUB reacts really slow. I am not ridiculous enough to switch back on Windows, but I loose the potential of a computer here. One of my favourite .... :(

To describe the problem a little:
I thought that it was a problem between the cordless keyboard and Ubuntu. I looked first on a firmware issue. But once I plugged an external hard drive I noticed a really slow transfer. I also checked the keyboard on a my Ubuntu computer at work; it works fine.

It's obvioulsy a pb with linux HUB and the serial ports of the motherboards. 
What would be a solution ? 
ECHDI ?
ACPI ?
Driver ?

Thanks for any help

Cheers

Ben

---

### Post by nutsy.ben on 2010-08-29
Ok one option is to change the grub configuration.

You can add 'irqpoll' to the boot command and it solves most of the problems.
Nevertheless, I have to admit that the motherboard is clearly not compatible with Ubuntu.

Cheers


Ben

---

