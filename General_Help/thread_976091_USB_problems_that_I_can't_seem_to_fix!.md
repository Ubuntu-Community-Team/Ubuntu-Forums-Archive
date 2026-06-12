---
title: "USB problems that I can't seem to fix!"
date: 2008-11-09
forum: General Help
---

### Post by ashleydangerous on 2008-11-09
Basically, I'm using Ubuntu 8.10 and have a USB headset that will randomly stop working and refuse to work again until I reboot, even after I plug it back in (the red power light won't even go on.)  I also have a USB webcam that won't work at all, even though it used to work just fine.

I've tried:
[LIST]
[*]Adding uhci_hcd to the modprobe blacklist
[*]Reinstalling any packages I could find relating to USB
[*]Running Skype and webcam apps with the LD_PRELOAD commands recommended in the stickied ibex post
[/LIST]

None of these seem to help at all :(  I'd really appreciate the help, as I spend a lot of time teleconferencing with coworkers and these USB problems are really becoming problematic.

Please let me know if you have any ideas, and I will try to implement them.

Thanks a ton! :)

---

### Post by easoukenka on 2008-11-09
Maybe if you can post some related dmesg information and lsusb we could be more help.  Are you using ports on the front or back because even though I have new computer my front ports will not work with some things properly like webcam and external drive.  Not sure why.

---

### Post by ashleydangerous on 2008-11-09
Hello!  I tried plugging the webcam into the back port of the computer, and the same thing happens -- Skype shows a garbled green screen.  I installed cheese, and the video seems to work there.

I searched the forums, and tried:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype

but the garbled greenness is still there in Skype.

Anyways, here is the information from the commands you mentioned!  The headset hasn't decided to stop working on its own yet, but when it does I will check dmesg and report back.

Here is information from lsbusb:

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 093a:2464 Pixart Imaging, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 046d:0a0c Logitech, Inc. 
Bus 001 Device 005: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 001 Device 004: ID 045e:0053 Microsoft Corp. Optical Mouse
Bus 001 Device 002: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Here are some usb-related things from dmesg (I unplugged the camera and headset, and then plugged them back in):

[45253.477085] usb 1-2.3: USB disconnect, address 6
[45265.468133] usb 1-1.1: new full speed USB device using ehci_hcd and address 8
[45265.606860] usb 1-1.1: configuration #1 chosen from 1 choice
[45265.661192] input: Logitech Logitech USB Headset as /devices/pci0000:00/0000:00:10.3/usb1/1-1/1-1.1/1-1.1:1.3/input/input10
[45265.688394] input,hidraw3: USB HID v1.00 Device [Logitech Logitech USB Headset] on usb-0000:00:10.3-1.1
[45266.276082] usb 1-2.4: USB disconnect, address 7
[45266.281266] gspca: disconnect complete
[45266.675498] cannot submit datapipe for urb 0, error -28: not enough bandwidth
[45279.601106] usb 1-2: USB disconnect, address 3
[45290.200046] usb 2-2: new full speed USB device using uhci_hcd and address 2
[45290.454325] usb 2-2: configuration #1 chosen from 1 choice
[45290.458166] gspca: probing 093a:2464
[45290.461098] pac207: Pixart Sensor ID 0x27 Chips ID 0x00
[45290.461110] pac207: Pixart PAC207BCA Image Processor and Control Chip detected (vid/pid 0x093A:0x2464)
[45290.472786] gspca: probe ok

Dmesg Without ehci_hcd blacklisted:

[    5.245959] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:10.3/usb1/1-1/1-1.2/1-1.2:1.0/input/input1
[    5.260339] input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:10.3-1.2
[    5.268250] input: Microsoft Natural&#65533; Ergonomic Keyboard 4000 as /devices/pci0000:00/0000:00:10.3/usb1/1-1/1-1.3/1-1.3:1.0/input/input2
[    5.268728] input,hidraw1: USB HID v1.11 Keyboard [Microsoft Natural&#65533; Ergonomic Keyboard 4000] on usb-0000:00:10.3-1.3
[    5.280071] input: Microsoft Natural&#65533; Ergonomic Keyboard 4000 as /devices/pci0000:00/0000:00:10.3/usb1/1-1/1-1.3/1-1.3:1.1/input/input3
[    5.280536] input,hidraw2: USB HID v1.11 Device [Microsoft Natural&#65533; Ergonomic Keyboard 4000] on usb-0000:00:10.3-1.3
[    5.282167] input: Logitech Logitech USB Headset as /devices/pci0000:00/0000:00:10.3/usb1/1-2/1-2.3/1-2.3:1.3/input/input4
[    5.282803] input,hidraw3: USB HID v1.00 Device [Logitech Logitech USB Headset] on usb-0000:00:10.3-2.3
[    5.282841] usbcore: registered new interface driver usbhid
[    5.282846] usbhid: v2.6:USB HID core driver
[   17.403168] usbcore: registered new interface driver pac207
[   17.640171] usbcore: registered new interface driver snd-usb-audio

---

### Post by easoukenka on 2008-11-10
I will look into this have you tried ekiga?  My father has problems with completely green webcam only ekiga works for him.

---

### Post by lisati on 2008-11-10
This reads a little bit like a problem I had with a mouse and a keyboard when useing Feisty (Ubuntu 7.04). The solution is described here: [http://ubuntuforums.org/showthread.php?t=854684](http://ubuntuforums.org/showthread.php?t=854684)

---

### Post by ashleydangerous on 2008-11-11
> **easoukenka said:**
> I will look into this have you tried ekiga?  My father has problems with completely green webcam only ekiga works for him.



I tried Ekiga, and it said:

Error while opening video device CIF Single Chip     

Running it with the following fixed it, though:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so ekiga


> 
This reads a little bit like a problem I had with a mouse and a keyboard when useing Feisty (Ubuntu 7.04). The solution is described here: [http://ubuntuforums.org/showthread.php?t=854684](http://ubuntuforums.org/showthread.php?t=854684)


I will try that, thank you :)

---

