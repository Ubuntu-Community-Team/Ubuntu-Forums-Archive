---
title: "Reading from USB device is tortuously slow"
date: 2007-02-19
forum: Hardware &amp; Laptops
---

### Post by martinquested on 2007-02-19
I am running 32-bit edgy on a Compaq Presario V6030US (V6000 series).

I have a cheap mp3 recorder which I regularly use to make recordings of up to 10MB in size.  At the moment, transferring these from the device to the laptop via the USB cable takes about 20 minutes per file, most of which time the thing seems to spend "stalled".  It means that every week I have to boot into XP so that I can download the files in under 30 seconds - most annoying to need to do this.

I have already found posts on similar topics (to do with writing to USB devices) and have already ensured the device is now mounted with the "sync" option switched off, and I have also disabled ohci to ensure that I get the fast usb driver.

Any other suggestions anyone?

---

### Post by timcredible on 2007-02-19
i've only seen the stalled message when using a usb 2.0 device on a usb 1.x port.  apparently, usb 2.0 devices really don't like to be plugged into a usb 1.x port.

---

### Post by martinquested on 2007-02-20
It ***ought*** to be a USB 2.0 port!!  How do I ensure that this is what Linux thinks it is?

---

