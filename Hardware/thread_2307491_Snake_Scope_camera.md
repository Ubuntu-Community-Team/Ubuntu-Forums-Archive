---
title: "Snake Scope camera"
date: 2015-12-25
forum: Hardware
---

### Post by timswait on 2015-12-25
I've just got an endoscope camera from Maplin:
[http://www.maplin.co.uk/p/flexible-snake-scope-camera-n41gw]("http://www.maplin.co.uk/p/flexible-snake-scope-camera-n41gw")

I believe this uses the same electronics as this which is described as fully Linux compatible:
[http://www.linux-hardware-guide.com/uk/2014-02-02-somikon-snake-scope-usb-endoscope-camera-vga-with-goose-neck]("http://www.linux-hardware-guide.com/uk/2014-02-02-somikon-snake-scope-usb-endoscope-camera-vga-with-goose-neck")

lsusb return includes this:
```
Bus 001 Device 002: ID 093a:2620 Pixart Imaging, Inc. 

```

I have Cheese and Kamosa installed (on Kubuntu Wily Werewolf) however while both detect the endoscope (they list "USB Camera (093a:2620)(/dev/video0) ) but whenever I try to display the image from the endoscope I just get a blank screen (if I select the built in webcam I get an image fine).
I have libv4l installed, what else can I do?

---

### Post by timswait on 2015-12-25
Hmmm, it works fine with the desktop (also on Wily Werewolf) but not the laptop. Annoying, if it was the other way round I'd be happy!

---

### Post by Vladlenin5000 on 2015-12-25
Some similar cameras have issues with certain USB3.0 ports. You may try an USB2.0 port if available.

---

### Post by timswait on 2015-12-26
I've tried it in all three of the USB ports on the laptop, I think two of them are USB3.0 and one is USB2.0, none of them work.

---

### Post by timswait on 2015-12-26
I've also tried using xsane but that can't see any devices available.

---

### Post by tokyobadger on 2015-12-26
> **timswait said:**
> Hmmm, it works fine with the desktop (also on Wily Werewolf) but not the laptop. Annoying, if it was the other way round I'd be happy!
I'd compare dmesg from the desktop and the laptop to try and see how the endoscope is being handled differently

Just a few additional thoughts to eliminate differences between the desktop and the laptop:
- both Kubuntu Wily
- both on the same kernel version
- any significant software differences between the 2 machines

The laptop's built-in camera might be creating a conflict - is it possible to disable the built-in camera in the BIOS?

---

### Post by coldraven on 2015-12-27
Try installing guvcview
```
sudo apt-get install guvcview
```

Run guvcview and try adjusting the brightness and also uncheck any "Auto level" boxes. If that works then just quit guvcview, no need to save anything, then try again with Cheese.

---

### Post by timswait on 2015-12-27
guvcview also doesn't get anything from the camera.
The dmesg does show an error when I plug in the camera to the laptop (which doesn't work):
```
[ 1122.056224] usb 1-3: new full-speed USB device number 3 using xhci_hcd
[ 1122.168273] usb 1-3: device descriptor read/64, error -71
[ 1122.401960] usb 1-3: New USB device found, idVendor=093a, idProduct=2620
[ 1122.401969] usb 1-3: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[ 1122.402378] usb 1-3: ep 0x83 - rounding interval to 256 microframes, ep desc says 400 microframes
[ 1122.402395] usb 1-3: ep 0x4 - rounding interval to 256 microframes, ep desc says 400 microframes
[ 1122.402784] gspca_main: gspca_pac7302-2.14.0 probing 093a:2620
[ 1122.403519] input: gspca_pac7302 as /devices/pci0000:00/0000:00:14.0/usb1/1-3/input/input20
```

In contrast when I plug it into the desktop (which does work):
```

[  161.187101] usb 5-5: new full-speed USB device number 3 using ohci-pci
[  161.349704] usb 5-5: New USB device found, idVendor=093a, idProduct=2620
[  161.349712] usb 5-5: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[  161.415942] media: Linux media interface: v0.10
[  161.437660] Linux video capture interface: v2.00
[  161.446467] gspca_main: v2.14.0 registered
[  161.447828] gspca_main: gspca_pac7302-2.14.0 probing 093a:2620
[  161.454856] input: gspca_pac7302 as /devices/pci0000:00/0000:00:12.0/usb5/5-5/input/input15
[  161.455154] usbcore: registered new interface driver gspca_pac7302
[  161.522073] usbcore: registered new interface driver snd-usb-audio

```

So why does the desktop recognise it, but not the laptop? Both are the same version of Kubuntu (15.10) and both the same kernel (4.2.0-22-generic).

---

### Post by timswait on 2015-12-27
Could it be lack of power from the USB port?

---

### Post by Vladlenin5000 on 2015-12-27
Is it the same with the USB2.0 port? If you really have one, that is.

xhci_hcd => USB3.0
ohci-pci => USB2.0

Of course, I'm not sure what the problem really is but all things and troubleshooting you did so far considered, it surely looks like it.

---

### Post by Vladlenin5000 on 2015-12-27
> **timswait said:**
> Could it be lack of power from the USB port?

Naah... The other way around is much more plausible.
It works fine in the desktop's USB2.0 (up to 500mA) and doesn't in the laptop's USB3.0 (up to 900mA).

---

### Post by timswait on 2015-12-27
That's odd. There's 3 USB ports on the laptop, one on the right and two on the left. The manual says the one on the right is USB2.0 and the two on the left may be USB2.0 or USB3.0 depending on precise model spec. The one on the right is black coloured, one of the ones on the left is black and one is blue. None of them say anything about Super Speed next to them. I had always assumed the blue one was the only USB3.0 and the other two were USB2.0. However whichever of the three ports I plug the camera into it comes up with xhci_hcd. So does this mean that all three ports are USB3.0 despite what the manual and the colour coding say?

---

### Post by timswait on 2015-12-27
The blue one has 5 conductors in the socket, the two black ones have only 4, so I'm pretty certain the blue one is the only USB3.0 port. So why is it that when I plug it into what is definitely a USB 2.0 port does it come up with:
```
usb1-3: new full-speed USB device number 11 using xhci_hcd 
```
This may be the root of why it's not working. Can I force it to accept that it is really a USB2.0 port?

---

### Post by Vladlenin5000 on 2015-12-27
Weird indeed... I agree with you, the color codes and the number of connectors certainly suggests that.
Could it be that all ports are part of the same (v3.0) hub? I don't know if this is even possible but would explain why the OS is using the same driver.

---

### Post by timswait on 2015-12-27
Whichever port I plug it into, it appears as being on "Bus 001" when I do "lsusb". Does this mean it's the same hub? Would getting something like this: [http://www.maplin.co.uk/p/belkin-usb-4-port-powered-desktop-hub-a90qy]("http://www.maplin.co.uk/p/belkin-usb-4-port-powered-desktop-hub-a90qy") and plugging it in via that make sure that it's connected as USB 2.0?

---

### Post by Vladlenin5000 on 2015-12-27
The same bus seems to suggest it's the same hub but I'm not sure. I don't know. Ditto about the use of an external USB hub.
My knowledge about hardware is limited.

---

### Post by tokyobadger on 2015-12-27
> **timswait said:**
> The blue one has 5 conductors in the socket, the two black ones have only 4, so I'm pretty certain the blue one is the only USB3.0 port. So why is it that when I plug it into what is definitely a USB 2.0 port does it come up with:
```
usb1-3: new full-speed USB device number 11 using xhci_hcd 
```
This may be the root of why it's not working. Can I force it to accept that it is really a USB2.0 port?

I **think** you can change the XHCI to ECHI in BIOS <-- no promises

---

### Post by timswait on 2015-12-27
Yes, setting the XHCI to "Disabled" in the BIOS has made the camera work! Just means I have to switch the BIOS back if I want to use anything that is USB3.0, but at least the camera works on the laptop now. Cheers all.

---

### Post by Vladlenin5000 on 2015-12-27
Great news :-)

Now you can go to the thread tools in the first post and mark it as solved.

---

### Post by tokyobadger on 2015-12-27
Good to hear the camera's working. We'd need someone more expert to provide a more complete solution ie working camera and USB3.0

---

