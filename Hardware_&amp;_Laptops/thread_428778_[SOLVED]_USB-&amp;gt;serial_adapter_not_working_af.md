---
title: "[SOLVED] USB-&amp;gt;serial adapter not working after upgrade to Feisty"
date: 2007-04-30
forum: Hardware &amp; Laptops
---

### Post by pinkunicorn on 2007-04-30
I have a USB->serial adapter that has been working flawlessly out of the box with Edgy and (IIRC) Dapper. After upgrading to Feisty, I get the following in /var/log/messages:

```
Apr 30 11:10:51 localhost kernel: [236131.524000] usb 3-2: new full speed USB device using uhci_hcd and address 6
Apr 30 11:10:51 localhost kernel: [236131.720000] usb 3-2: configuration #1 chosen from 1 choice
Apr 30 11:10:51 localhost kernel: [236131.724000] ftdi_sio 3-2:1.0: FTDI USB Serial Device converter detected
Apr 30 11:10:51 localhost kernel: [236131.724000] drivers/usb/serial/ftdi_sio.c: Detected FT232BM
Apr 30 11:10:51 localhost kernel: [236131.724000] usb 3-2: FTDI USB Serial Device converter now attached to ttyUSB0
Apr 30 11:10:55 localhost kernel: [236135.852000] usb 3-2: usbfs: interface 0 claimed by ftdi_sio while 'brltty' sets config #1
Apr 30 11:10:57 localhost kernel: [236135.852000] ftdi_sio 3-2:1.0: device disconnected
Apr 30 11:29:34 localhost kernel: [237251.540000] usb 3-2: USB disconnect, address 6

```

If I manage to talk to my serial device in the period before the device disconnects it works, but it still disconnects. Apparently the driver as such can still talk to the hardware, but for some reason it bails out automatically.

How can I fix this? Or is this a bug?

---

### Post by CRCarl on 2007-05-03
I looked around and found this - 

```
sudo aptitude remove brltty
```

The first solution involved removing ubuntu-desktop so I skipped that one, the second solution worked well. 

brltty is used to drive a braille screen reader, so if you are not using one you can remove it safely. 

Craig

---

### Post by VeeDubbss on 2007-05-07
I was having the exact same problem.  Removing brltty fixed it!  Thanks!

---

### Post by newpants2003 on 2007-07-25
> **CRCarl said:**
> I looked around and found this - 

```
sudo aptitude remove brltty
```

The first solution involved removing ubuntu-desktop so I skipped that one, the second solution worked well. 

brltty is used to drive a braille screen reader, so if you are not using one you can remove it safely. 

Craig


THANK YOU SO MUCH!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

spend two days reading big articles.....

---

### Post by cnlohfin3109 on 2007-08-03
woot! thanks so much!:KS

---

