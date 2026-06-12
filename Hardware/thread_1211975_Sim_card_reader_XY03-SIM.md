---
title: "Sim card reader XY03-SIM"
date: 2009-07-13
forum: Hardware
---

### Post by bwucke on 2009-07-13
I have the sim card reader mentioned in the title.
Unfortunately, none of the solutions mentioned in the thread [http://ubuntuforums.org/showthread.php?t=650326](http://ubuntuforums.org/showthread.php?t=650326) work. (and the forum won't let me post a new reply, thus new thread).
 
The reader appears as USB serial device. It works fine with Windows. 

```

[21133.760095] usb 2-1: new full speed USB device using uhci_hcd and address 3
[21133.964630] usb 2-1: configuration #1 chosen from 1 choice
[21133.967201] pl2303 2-1:1.0: pl2303 converter detected
[21133.993297] usb 2-1: pl2303 converter now attached to ttyUSB0

```Monosim simply says "no PCSC smartcard reader found on pc".

Any way to get it to work?

---

### Post by zydar on 2010-10-08
any idea ? so . . up ?

---

### Post by dcstar on 2011-01-15
> **zydar said:**
> any idea ? so . . up ?

Install the **libtowitoko2** package.

Monosim sees my PL2303 device with this installed, but it does not detect a SIM on my setup.

---

