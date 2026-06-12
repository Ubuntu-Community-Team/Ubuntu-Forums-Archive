---
title: "[SOLVED] HP Photosmart Not Being Detected"
date: 2008-09-25
forum: Hardware
---

### Post by Circus-Killer on 2008-09-25
previously, i have used my HP printer/scanner perfectly in ubuntu. it was able to print and scan images.

however, for some reason now, on my fresh install, when i plug in the printer ubuntu does not recognise it. previously, when i plugged the printer in, it would pick it up straight away. anyone perhaps know of a reason why it suddenly wont detect my printer?

---

### Post by Sef on 2008-09-25
1) What kind of Photosmart is it?

2) What version of Ubuntu are you using?

---

### Post by phidia on 2008-09-25
What does > lpstat -p entered in a terminal output?

---

### Post by Circus-Killer on 2008-09-26
its an hp photosmart 3210. (its worked 100% previously)
i'm currently running hardy.

unfortunately, i cannot run the lpstat command now cos i'm at work. i will do that this evening and paste the output.

---

### Post by Circus-Killer on 2008-10-10
sorry for taking so long to response.
lpstat only return the PDF printer, no actual printers.

the only useful information i could get was from dmesg:
```

[   73.011084] usb 4-1: new full speed USB device using uhci_hcd and address 12
[   73.013305] usb 4-1: device descriptor read/64, error -71
[   73.017879] usb 4-1: device descriptor read/64, error -71
[   73.021331] usb 4-1: new full speed USB device using uhci_hcd and address 13
[   73.030776] usb 4-1: device not accepting address 13, error -71
[   73.032637] usb 4-1: new full speed USB device using uhci_hcd and address 14
[   73.047291] usb 4-1: device not accepting address 14, error -71
[   74.311803] usb 3-1: new full speed USB device using uhci_hcd and address 2
[   74.313799] usb 3-1: device descriptor read/64, error -71
[   74.316939] usb 3-1: device descriptor read/64, error -71
[   74.319971] usb 3-1: new full speed USB device using uhci_hcd and address 3
[   74.322212] usb 3-1: device descriptor read/64, error -71
[   74.333816] usb 3-1: device descriptor read/64, error -71
[   74.352534] usb 3-1: new full speed USB device using uhci_hcd and address 4
[   74.370582] usb 3-1: device not accepting address 4, error -71
[   74.376118] usb 3-1: new full speed USB device using uhci_hcd and address 5
[   74.674849] usb 3-1: device not accepting address 5, error -71

```

i dont suppose this helps?
i have no clue why my printer is suddenly giving me these problems, i've never had a problem with it in the past.

---

### Post by Circus-Killer on 2008-10-14
*bump*

---

### Post by Sef on 2008-10-14
Have you tried plugging it into another usb slot?

---

### Post by Circus-Killer on 2008-10-14
> **Sef said:**
> Have you tried plugging it into another usb slot?

i think i did, but i'm only 95% sure.
will have to try when i get home (that's where the printer is).

will post back my results tomorrow morning.

---

### Post by fballem on 2008-10-14
Could you please check and see if HPLIP is installed on your system? Do do this, start Synaptic and do a search for 'hplip' - there is a version in the repositories.

It should come up and identify if it is installed or not, and the version number, which I think is 2.8.2 from the repositories.

If HPLIP is not installed, the version that is in the repositories should be installed - it's an old printer. This may fix your problem, assuming that it isn't already installed.

Hope this helps,

---

### Post by Circus-Killer on 2008-10-15
well, sef, your solution half-worked. after enough unplugging and plugging in, it eventually picked up my printer/scanner.

unfortunately, the scanner functions didnt work at all, but im still playing around to see if i can get it working properly.

as for hplip, it is definately installed, so thats not the problem.

will report back when ive tried out the scanner functions some more.

---

### Post by Circus-Killer on 2008-10-16
thanks again sef, everything seems to be running 100%.
it's weird that all i had to change to a different usb port. cos that usb port works for pretty much all my other hardware.

anyways, thanks to those who helped, this thread is now solved. :D

---

