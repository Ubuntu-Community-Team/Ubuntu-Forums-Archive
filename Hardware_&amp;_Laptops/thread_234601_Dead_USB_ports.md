---
title: "Dead USB ports?"
date: 2006-08-11
forum: Hardware &amp; Laptops
---

### Post by br77 on 2006-08-11
I recently installed Dapper Drake on a new laptop (kernel 2.6.15-26-686), and nothing happens when I plug anything (my thumbdrive, a mouse, or my Nikon D50 camera) into a USB port. Nothing appears to automatically mount, nothing changes in the device manager (as far as I can tell), there is no /dev/sd* registered, and tail -f /var/log/messages doesn't change. USB support is enabled in the BIOS, but I don't have Windows on this machine to test if the ports work with that OS (although all of the devices work on my other laptop).

Is there any other way to tell if my USB ports are working with linux, or should I just put a multimeter to the pins (and would that even confirm the nightmare that both of the USB ports could be dead)?

I do have a FreeDOS bootdisk. Does anyone know how to test the USB ports with DOS?

Brian

---

