---
title: "How do I downgrade to USB 1.1.. or whatever the correct way to say that is"
date: 2009-04-13
forum: Hardware
---

### Post by samclark on 2009-04-13
I just installed ubuntu and one of my devices doesn't work. My Linux experience is minimal. I suspect it's related to high speed communication problems in the kernel (I'm not talking out of my *** I'm actually using an external protocol analyzer) and I've been told something along the lines of "USB 2.0 support in Ubuntu is spotty and it should work if you remove/disable the USB module and revert to USB 1.1". I just want to see if this is true and I'm not seeing any clear instructions poking around with google. I'm sure some of that's probably a lingo problem.

I've seen mentions of a BIOS setting but I don't see anything obviously usb related in my BIOS setup screen. Can anyone tell me how to revert to USB 1.1 only?

---

### Post by unutbu on 2009-04-13
I refer you to this page:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/49367](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/49367)

and in particular, Tristan BENOIST's comment:

> To temporary solve the problem, disable USB 2.0 by this way :
```
sudo modprobe -r ehci_hcd
sudo echo "blacklist ehci_hcd" > /etc/modprobe.d/blacklist-ehci
```
The first line removes the ehci_hcd module from the kernel. This is the module that enables USB 2.0. The second line tells the kernel not to load the module at boot time. So it is permanently disabled until you do this:

To get USB 2.0 back :
```
sudo rm /etc/modprobe.d/blacklist-ehci
sudo modprobe ehci-hcd
```

---

### Post by samclark on 2009-04-15
Thank you sir.

If the blacklist-ehci file doesn't exist can I just write to plain ol' blacklist instead?

---

### Post by unutbu on 2009-04-15
Yes, you could write to /etc/modprobe.d/blacklist instead of creating /etc/modprobe.d/blacklist-ehci.

I think Tristan Benoist's use of blacklist-ehci is kind of nice though, because it lets you disable/enable ehci without having to edit any files.

---

### Post by samclark on 2009-04-15
Does that mean the kernel will parse all the files under modprobe.d on startup for blacklisted modules (among other things) regardless of the file names?

I wasn't sure how to the kernel association with the newly created blacklist-ehci file would be specified.

---

### Post by unutbu on 2009-04-15
Yes, that's correct. Every file in /etc/modprobe.d gets parsed.

---

### Post by randa486 on 2011-01-14
> **unutbu said:**
> I refer you to this page:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/49367](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/49367)

and in particular, Tristan BENOIST's comment:

FATAL: Module ehci_hcd is builtin

how can i solve the problem

---

