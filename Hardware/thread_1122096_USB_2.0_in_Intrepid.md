---
title: "USB 2.0 in Intrepid"
date: 2009-04-10
forum: Hardware
---

### Post by evilkillerfiggin on 2009-04-10
I'm having problems with a USB device on my laptop, because it wants USB 2.0 ports and, according to lsusb, all the ones I have available are 1.1. (I'm pretty sure this is the problem as I've confirmed the device works on another Ubuntu box.)

Thing is, my laptop is relatively new, and it was my understanding that USB 1.1 is incredibly old. Therefore, I'm asking is it possible that the hardware I've got is 2.0 and yet Ubuntu is treating it like 1.1?

If this is the case, how would I fix it?

---

### Post by 0cton on 2009-04-10
how new is your laptop?
It is higly unlikely that ubuntu wont recognise it
and usb 2.0 is backwards compatible with 1.1 and 1.0 at the cost of speed :)

---

### Post by evilkillerfiggin on 2009-04-10
No, no, other way around. I have 1.1s, which are pointedly not forward compatible with 2.0. So now it looks like I've gotta mess around with hardware I don't understand...

The output of lsusb is:
```

tog@dell-desktop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 007: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 004 Device 006: ID 04a9:2220 Canon, Inc. CanoScan LIDE 25
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

That's nine entries, but I only have four ports on my laptop. It's a Dell Inspiron 1525.

Anyone know what those five extra entries are likely to be? And if there's anyway I can get at either of those 2.0s at the top?

---

### Post by Chemical Imbalance on 2009-04-10
I believe--correct me if I'm wrong--that the kernel uses 1.1 on that hub if a 1.1 device is plugged in to save power.  That's what I'm assuming, because on all of my computers (with only 2.0 hubs) this happens to me also when a 1.1 usb device is plugged in.

That's just my guess though.

---

### Post by evilkillerfiggin on 2009-04-10
Ah. Any idea why, when I plug a 2.0 device in, it wouldn't pick it up?

---

### Post by Chemical Imbalance on 2009-04-10
I'm gonna have a look at this site, looks like it may have the answers:
[http://www.linux-usb.org/](http://www.linux-usb.org/)

---

### Post by evilkillerfiggin on 2009-04-11
Okay, I read through the site, but I'm afraid a good deal of it went over my head.

Is there anyway to tell, decisively, what model each of my USB ports are?

---

### Post by Chemical Imbalance on 2009-04-11
> **evilkillerfiggin said:**
> Okay, I read through the site, but I'm afraid a good deal of it went over my head.

Is there anyway to tell, decisively, what model each of my USB ports are?

Try finding the support page from your manafacturer and look for a downloadable pdf manual if you don't have one yourself.

---

### Post by evilkillerfiggin on 2009-04-12
Okay, I have affirmed that I have at least two USB 2.0s on the side of my laptop. This then has to be a problem with Ubuntu, yes?

Where do I go from here? What info/action is needed to sort this out?

---

### Post by Chemical Imbalance on 2009-04-13
I really don't know because I'm also wondering why they show up as 1.1 hubs too.  Perhaps someone out there knows?  Anyone?

---

