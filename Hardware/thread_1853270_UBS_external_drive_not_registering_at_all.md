---
title: "UBS external drive not registering at all"
date: 2011-10-01
forum: Hardware
---

### Post by WarrenSensei on 2011-10-01
Ok, so I'm trying to access an old USB external, full-format hard drive (regular internal drive in an external USB housing). It works fine on my old desktop system (also running Ubuntu, but that 11y/o box is barely functional anymore, having a heavily damaged hard drive from a nasty virus back when it used to be a Window$ box). However, I have yet to get it to even show up in lsusb on any laptop system running Ubuntu.

I don't have a brand, but it's one of the types with its own power supply (not using a powered USB port). I have opened the housing and everything seems to be in order, though the drive "jumpers" are set to "drive 0 - Master" which seems odd to me for an external drive, but what do I know?

I've attached a zipped txt with the dmesg output after a restart with the device plugged in (and on!), then moving the usb to another port.

Running Ubuntu 11.04.

An help or suggestions would be greatly appreciated, thank you!
~Warren

---

### Post by coffeecat on 2011-10-02
> **WarrenSensei said:**
> though the drive "jumpers" are set to "drive 0 - Master" which seems odd to me for an external drive,

That's OK. All the USB enclosures for IDE/PATA drives I've used require the drive to be set to master, otherwise it doesn't work.

> **WarrenSensei said:**
> I've attached a zipped txt with the dmesg output after a restart with the device plugged in (and on!), then moving the usb to another port.

Curious - the system doesn't even seem to be detecting it. Just to be sure, do a fresh boot without the USB plugged in, then plug the USB drive in and switch it on, wait a few seconds and then:

```
dmesg | tail
```

Post the output between [noparse]```
 and 
```[/noparse] tags. It's bit easier for everyone than fiddling with zip files. :wink:

> **WarrenSensei said:**
> (also running Ubuntu, but that 11y/o box is barely functional anymore, having a heavily damaged hard drive from a nasty virus 

I wouldn't have thought a virus could do physical damage. Have you tried completely zeroing the drive?

---

