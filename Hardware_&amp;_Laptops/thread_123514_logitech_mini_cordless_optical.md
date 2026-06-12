---
title: "logitech mini cordless optical"
date: 2006-01-30
forum: Hardware &amp; Laptops
---

### Post by gdcondor on 2006-01-30
Hi !

I just bought a logitech mini cordless optical mouse (usb).
I followed instructions from [http://ubuntuforums.org/showthread.php?t=65471](http://ubuntuforums.org/showthread.php?t=65471)

But I'm having problems right at the beginning : when I plug the mouse I can see it in "cat /proc/bus/input/devices" with "Handlers=mouse1 event2 ts1"
But if i try "cat /dev/input/mouse1" (or event2, ts1 or any other file in /dev/input) while moving the mouse I don't see any output :(((
Any idea why ? i've a standard breezy with standard kernel : the modules usbhid, usbcore, ehci_hcd, uhci_hcd, evdev are loaded...

Thanks for your help ! (i tried on 2 different computers using ubuntu breezy)
-- 
Florian

---

### Post by gdcondor on 2006-02-05
I just pressed the "reset" button on the mouse and it's working perfectly : what a stupid problem :)

---

