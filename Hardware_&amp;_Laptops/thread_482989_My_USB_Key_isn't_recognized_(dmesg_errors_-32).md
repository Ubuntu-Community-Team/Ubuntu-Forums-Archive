---
title: "My USB Key isn't recognized (dmesg errors -32)"
date: 2007-06-24
forum: Hardware &amp; Laptops
---

### Post by Excelsior89 on 2007-06-24
Hello. I got several problems with my USB Key CORSAIR Voyager 16Go.
If I plug it while i'm under ubuntu, it's not working. When I perform a dmesg I got this

```
[1277237.415934] usb 2-6: new high speed USB device using ehci_hcd and address 6
[1277239.431734] usb 2-6: device descriptor read/64, error -32
[1277239.651709] usb 2-6: device descriptor read/64, error -32
[1277239.867692] usb 2-6: new high speed USB device using ehci_hcd and address 7
[1277239.983677] usb 2-6: device descriptor read/64, error -32
[1277240.203659] usb 2-6: device descriptor read/64, error -32
[1277240.419637] usb 2-6: new high speed USB device using ehci_hcd and address 8
[1277240.827595] usb 2-6: device not accepting address 8, error -32
[1277240.939583] usb 2-6: new high speed USB device using ehci_hcd and address 9
[1277241.347535] usb 2-6: device not accepting address 9, error -32
```
It's always exactly the same scheme, 2 times  "device descriptor read/64, error -32" and 2 times "device not accepting address X, error -32" each time I'm pluging the key.

I've tried to plug it on others usb port, I've tried disabling ACPI and APIC, also the kernel 2.6-21. But nothing changes, it's always the same problem.

In fact, there is one thing I can do to make the key work (merely) perfectly.
If I plug the key while starting up the computer (before grub launches), then the key is well recognized and I can use it, mount and unmount partitions without any problems. Of course, if I unplug it, there's no way to make it work anymore when I replug it.

I don't know what to do with that. I don't know if I should report that bug on launchpad or not, as I'm not sure of wich component fails in my problem. If you have any idea, I'm here :)

PS : Key works very well under windows, I assume it's not damaged in any case.

---

### Post by Super TWiT on 2007-06-24
Did you compile your own custom kernel?  The reason I am asking is because one time when I compiled my own kernel it did exactly that.  Try booting one of the kernels Ubuntu released and see if the same thing happens.

---

### Post by gator on 2007-06-24
i have issues with usb device's also ( and many other people) . my prob was related to usb2 - so please try this :- 
unplug devices
type ' sudo modprobe -r ehci_hcd ' 
now plug in devices

it worked for me -but only usb 1 speed.
good luck

---

### Post by kahlil88 on 2008-04-25
Is there a way to make it run at full speed? I really hate running at USB 1 speed.

---

### Post by Yellow Onion on 2008-05-03
on this thread some one has reported it as a bug.
[http://ubuntuforums.org/showthread.php?t=745672](http://ubuntuforums.org/showthread.php?t=745672)
[https://bugs.launchpad.net/ubuntu/+bug/211760](https://bugs.launchpad.net/ubuntu/+bug/211760)

---

