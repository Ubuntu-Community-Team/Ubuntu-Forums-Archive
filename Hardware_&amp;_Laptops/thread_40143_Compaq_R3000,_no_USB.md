---
title: "Compaq R3000, no USB?"
date: 2005-06-07
forum: Hardware &amp; Laptops
---

### Post by elmopuddy on 2005-06-07
HIya.

 I've tried many distros, but since none give USB, and Ubuntu is my fav, I decided to post here..

 No matter if I use 32 or 64 bit version, I have no USB at all.. I am somewhat new to linux, so please tell me what info you need to help out..

 The laptop has a A64 3200+, GIG ram, NForce 3 chipset.. 5.04 64 bit is installed right now, default 2.6.10.5 kernel.

Thanks in advance.

EP

---

### Post by mobile.army on 2005-06-08
That's a bit bizarre... I think Linux has supported USB since 2.4 (at least).

A few questions:
-Are you sure the problem is your USB and not the devices you're plugging into it? (What have you tried to use with the USB?)

-Are any USB hubs or chipsets appearing when you go to System>Administration>Device Manager?

-When Ubuntu is starting up and gets to the section about starting Hotplug (I don't remember the phrase it uses), do you get an OK?

The answers will help the response of others.

---

### Post by elmopuddy on 2005-06-08
hmmm,

1. I've tried a few devices: mice, keyboards, USB drives, all devices that work on my A64 Ubuntu desktop

2. Under device manager I see 3 USB entries: Nforce3 USB 1.1 (x2), and Nforce3 USB 2.0

3. At bootup, hotplug subsystem loads OK.

EP

---

### Post by elmopuddy on 2005-06-08
ok, some progress..

I was running 2.6.10.5-amd64-generic kernel, upgraded to 2.6.11-1-K8..

- USB drive (1 GIG Lexar JumpDrive) now works!
- USB mice (Intellimouse Explorer 1.0, and Logitech Optical mouse) do not work

USB mice are lit up until hotplug subsystem loads, then they shut off.

On another note, after kernel patch, touchpad very lethargic.

EP

---

### Post by mobile.army on 2005-06-08
I think now you just need to install the mouse. I assume you didn't have to do it with the desktop, but Ubuntu didn't install the same on my desktop and laptop (but Windows never did either).

---

