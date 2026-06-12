---
title: "What to do if a USB device is not detected ?"
date: 2011-04-02
forum: Hardware
---

### Post by arunb on 2011-04-02
Hi,

Platform: Ubuntu 10.04

I have a USB TV Tuner (ENTER). The device is not detected by 10.04, I tried lsusb and could not find the device. Although the same device is detected by VirtualBox running Windows XP on the same machine.

I just what to know what are the basic steps involved in diagnosing USB based problems.

thanks
ar

---

### Post by matt_symes on 2011-04-02
Hi

Plug it in and type (at a terminal)

```
dmesg | tail -n40
```

Read the output to get some clues as to what is happening.

Kind regards

---

### Post by arunb on 2011-04-02
Here is the result. The last part is interesting it shows the insertion of the device.

> 
[  173.547963] usb 2-1.2: new high speed USB device using ehci_hcd and address 4
[  173.938981] usb 2-1.2: configuration #1 chosen from 1 choice


Now what should I do next...
thanks
a

---

### Post by matt_symes on 2011-04-02
Hi

> **arunb said:**
> Here is the result. The last part is interesting it shows the insertion of the device.

Now what should I do next...
thanks
a

Is that all the text in dmesg pertaining to the usb device ? What is the actual device ?

Kind regards

---

### Post by arunb on 2011-04-03
dmesg gave out other entries, but I could not post them as I got a message saying the post had exceeded 14 images. So I had to edit out the previous entries and just post the last ones.

The device I am trying to use is a USB TV Tuner device, manufactured by ENTER. See link [http://www.enter-peripherals.com/tvtuner_stick.html]("http://www.enter-peripherals.com/tvtuner_stick.html")

I could not find Linux drivers for this device. I am aware this device is difficult to use with Linux, but as the device was given to me by a friend I had no choice in selecting a compatible device.

I have written to the company asking for a suitable Linux driver.

thanks in advance.

a

---

