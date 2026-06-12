---
title: "Laptop Touchpad does not work under ubuntu 12.10"
date: 2013-03-12
forum: Hardware
---

### Post by XkLi on 2013-03-12
Hello,

I have recently installed Ubuntu 12.10 and my Touchpad is not working.
I know that the hardware is working as it is perfeclty fine in Windows and Gentoo. 
After using ```
xinput
``` I got the following output: 

```
xkli@xkli-P15xEMx:~$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse             id=8    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; BisonCam, NB Pro                            id=6    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=7    [slave  keyboard (3)]
```

Please not that I currently have an external mouse connected. From my Windows side I know that my Touchpad is connected to a PS/2 port.

Any help on how I can activate it would be greatly appreciated

---

### Post by mikewhatever on 2013-03-13
Doesn't look like the touchpad is detected. Can you provide any info about the vendor.

---

### Post by XkLi on 2013-03-13
Hi, the touchpad is a Synaptics Touchpad and the Computer itself is from XMG. I also found out that Ubuntu does not recognize this Computer as  Laptop. The "close lid" options are missing in the power menu and even with tweak tools I cannot get my computer the suspend when the lid is closed. Can it be that all of this resulted from me having to install and always boot Ubuntu with acpi=off? The last thing is that I currently cannot boot into Ubuntu since it tells me that there is a problem mit my VGA. ANyy pointers on that?

---

### Post by mikewhatever on 2013-03-13
acpi=off is very possibly the cause of at least some of those problems. What happens if you enable acpi?

---

### Post by XkLi on 2013-03-13
when acpi=off is not enabled Ubuntu does not boot nor can I install it. I had to resort to acpi=off after nomodeset did not work nor did any of the other options.

---

