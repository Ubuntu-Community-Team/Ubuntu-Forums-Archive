---
title: "USB scanner keeps resetting and getting new USB device number"
date: 2005-11-21
forum: Hardware &amp; Laptops
---

### Post by dwhsix on 2005-11-21
Now, I know this may be an issue with the scanner, but I thought I'd try asking anyway.

I have this question also open on the sane list, but I'm trying to get an Epson Perfection 3490 scanner to work on Ubuntu 5.10.

I installed the Epson linux software and that seemed to  get me a little closer, but the weird thing right now is that it appears the scanner is resetting every few seconds and getting a new USB device number.  So dmesg is filled with entries like:

[4298471.383000] usb 5-1: new high speed USB device using ehci_hcd and address 118
[4298494.715000] usb 5-1: USB disconnect, address 118
[4298494.883000] usb 5-1: new high speed USB device using ehci_hcd and address 119
[4298536.465000] usb 5-1: USB disconnect, address 119

...etc...

Any suggestions as to why this might be happening?  Any pointers on what else I can do to try and investigate this?

Thanks,

dwh

---

### Post by oskude on 2005-11-22
try another usb cable/port...
does other usb hardware work ? (like flash-stick)

---

### Post by lompolo on 2005-12-01
look at this thread

[http://ubuntuforums.org/showthread.php?t=65656&highlight=epson+3490](http://ubuntuforums.org/showthread.php?t=65656&highlight=epson+3490)

I got it working partially, but I also need more help.

Let's try together

---

### Post by dwhsix on 2005-12-01
At the moment I have actually given up on getting the 3490 to work on Ubunutu... it's now plugged in to my wife's (Windows) machine, on the other side of our shared office.  But it's close enough to my machine that I can swap USB cables :-) .

There are definitely several people on the [sane-dev]("http://lists.alioth.debian.org/mailman/listinfo/sane-devel") list who have Epson 3490s working on Linux, and at least one on Ubuntu.

But so far the response I've gotten from that list has not been that helpful... since the device keeps resetting, people are asking whether there's a problem with hotplug management in Ubuntu or on my hardware.

But as far as I know other USB devices are working fine.  The digital camera is, and my mouse is also USB.  So I have no reason to think there's a problem on the USB host side.

As I said, I don't have the time to do any more work on it, given that I can run it on my wife's Windows machine.  I am hoping to get back to it at some point, though.

dwh

---

