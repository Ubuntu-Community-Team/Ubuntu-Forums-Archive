---
title: "Webcam not detected"
date: 2020-03-22
forum: Hardware
---

### Post by asearle on 2020-03-22
Hallo Everyone,

I fixed up a Lenovo Thinkpad T520 with Ubuntu 18.04 for a friend but we have found that the webcam is not recognised.

"Cheese" could not find the webcame and we ran "dmesg | grep usb" but there was no sign of it.

Can anyone help me with this? Maybe software/utilities that we can install? Or further diagnostics that we can run?

Many thanks,
Alan in Cologne

---

### Post by mörgæs on 2020-03-22
Please run ```
lsusb
``` and post the results in CODE tags.

---

### Post by asearle on 2020-03-22
I will try to get hold of that but, in the meantime, I ran "lsusb" on MY laptop (which has a working webcam) and there seemed to be no indication of the webcam ...

```
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 8087:0a2b Intel Corp. 
Bus 001 Device 003: ID 058f:3822 Alcor Micro Corp. 
Bus 001 Device 004: ID 046d:c064 Logitech, Inc. M110 corded optical mouse (M-B0001)
Bus 001 Device 002: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Or does one of the above indicate that a webcam is supported?

On MY laptop the command "dmesg | grep usb" returns a webcam ...

```
[   12.520791] input: HD Webcam: HD Webcam as /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/input/input11
```

But on the laptop I am diagnosing there is no line indicating a webcam.

Anyway, I will try to get the outputs from the laptop I am diagnosing: I need to get that output sent to me.

Yours,
Alan

---

### Post by mörgæs on 2020-03-23
> **asearle said:**
> 
```
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 8087:0a2b Intel Corp. 
Bus 001 Device 003: ID [COLOR=#ff0000]058f:3822[/COLOR] Alcor Micro Corp. 
Bus 001 Device 004: ID 046d:c064 Logitech, Inc. M110 corded optical mouse (M-B0001)
Bus 001 Device 002: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Or does one of the above indicate that a webcam is supported?



Try to google **"058f:3822" webcam** (including the quotes).

---

### Post by asearle on 2020-03-23
Many thanks: So, yes, my laptop is detecting my WebCam.

The laptop I am diagnosing returns this output ...

```
Bus 002 Device 003: ID 0bdb:1911 Ericsson Business Mobile Networks BV
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

... which doesn't seem to include the WebCam(?)

Does that mean that for some reason it is not physically connected? Or is faulty? Or are there other diagnostics that we can do?

Many thanks,
Alan

---

### Post by mörgæs on 2020-03-23
Just guessing here: Is it enabled in BIOS/UEFI?

On the computer where the camera is displayed: The command ```
sudo lsusb -v -d 058f:3822
``` shows a list of details (in case you need to investigate more).

---

### Post by asearle on 2020-03-28
Dear Moergaes,

Bingo! Yes, many thanks: It was switched off in the BIOS.

Indeed, I believe that this particular "friend" specifically requested that I completely deactivate the webcam ... for his security! Then a year or two later he complains to me that the webcam doesn't work.  Arrrggghhh! They can't have it both ways  :-)

Cheers,
Alan

---

