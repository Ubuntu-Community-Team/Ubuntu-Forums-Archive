---
title: "PCI Parallel Port adapter for MSI laptop (for running a CNC machine)"
date: 2011-10-23
forum: Hardware
---

### Post by dsoodak on 2011-10-23
Does anyone know where to find a PCI-E parallel port adapter for a laptop running ubuntu? At this point, having a driver already written for a Linux system is more important than price.

I am using a CNC machining program in rtai kernel and it doesn't seem likely that a usb-parallel device will have a fast enough response time(or will it? how much is usb latency in real-time mode?).

---

### Post by conradin on 2011-10-23
What are the specs of this device? model, brand, etc...
I've never heard of a PCIe laptop --> paraelle connector. 
Was this device working at some point in another verion of linux?
USB --> paraelle devices exist at about 20$ that might save you much time 
and effort to get some other crazy thing to work. Unless this is some Proprietary card made by the CNC machine vendor.. (is it?)
Tell us more about you hardware, does the CNC only have a paralle port?

also show us the result of the command ```
$ dmesg | tail
```

---

### Post by conradin on 2011-10-23
Aw darn I read that all wrong. Im pretty sure the data rates will be fine, what you might concern yourself with is the power specs of the CNC device, and its paraell port. If the cnc takes power from the paraelle port, then Ive seen issues with over current on the USB port. Desktops do not typicaly have that problem, with slightly more robust designs for built in paraelle ports. Still, needing of system specs though.

---

### Post by dsoodak on 2011-10-23
The CNC machine interface shouldn't be drawing any power from the PC.
The software is currently set up to not go more than about 400 hz pulses though this could be on X, Y, and Z axes(so total of 1200 hz communication), plus listening in on the axis travel limit switch lines(3: one for each axis).
Though USB has a fast transfer rate, it also has big latency so I'm not sure if a usb-parallel port adapter will be sufficient.
I currently have a usb-parallel adapter with a MCS7705 chip but the driver I downloaded won't compile so I haven't had a chance to test it out.

---

