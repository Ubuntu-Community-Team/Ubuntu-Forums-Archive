---
title: "Keyspan USA49W 4-port USB-Serial"
date: 2006-09-23
forum: Hardware &amp; Laptops
---

### Post by jmc1024 on 2006-09-23
Hello Everyone,
I'm a new convert.  I've used RedHat and Caldera (hey, I worked for a
sister company) for years.  Xubuntu worked on a box that RedHat and 
Caldera wouldn't install.  I also have it running on a VAIO FS760 
laptop.

Anyhow, I dusted off a Keyspan USA49W 4-port USB-Serial converter.  
I can't find any instruction of getting it to work.  dmesg show that 
it was detected but the firmware is not available.  Where can I find 
the firmware and what do I do with it when I get it?
dmesg:
   usb 1-2: new full speed USB device using ohci_hcd and address 13
   keyspan 1-2:1.0: Keyspan - (without firmware) converter detected
   usb 1-2: Required keyspan firmware image (USA49W) unavailable.

I'm really interested in getting this to work.  All help is 
appreciated.
Thanks,
Mark

---

### Post by jmc1024 on 2006-09-25
Hello, 

I'm answering my own question incase someone needs the same answer.  I recompiled the kernel with the firmware turned on in the config.

Mark

---

### Post by danbyte on 2006-11-13
How do you start a terminal session using the serial connection?

---

### Post by jmc1024 on 2007-05-06
I don't.  I use the serial connection for a weather station, a fax modem and such.  If I was going to use a terminal program to dial out, I'd use minix.  Or getty to "dial" in.
HTH,
Mark

---

### Post by blakesle on 2007-07-24
> **jmc1024 said:**
> Hello, 

I'm answering my own question incase someone needs the same answer.  I recompiled the kernel with the firmware turned on in the config.

Mark

Can you provide a more detailed set of instructions? I am trying to get a Keyspan serial to USB connector working and I have searched the threads on this site but only have very incomplete instructions. 

Any help you can provide would be appreciated.

Thanks,

Bruce

---

