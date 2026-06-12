---
title: "Video driver version information"
date: 2008-06-04
forum: Hardware
---

### Post by pcman312 on 2008-06-04
I'm writing a program to determine various system information in C++ and I'm having issues finding where I can get information regarding the display drivers, specifically the ATI drivers (or fglrx). I have been able to find the nvidia drivers, however I need to be able to determine either from the system. I do have one major restriction: I need it to run on a system right out of the box, no additional installation of programs.

If it matters, I am designing the program to run on Debian, although I doubt that in this case it will mater too much.

---

### Post by sdennie on 2008-06-04
I don't have any ATI cards to try this but, you should be able to get the driver information for any card by looking in /var/log/Xorg.0.log.  For example, for the nvidia proprietary driver, you can find the version information with:

```

grep "X Driver" /var/log/Xorg.0.log

```

---

### Post by pcman312 on 2008-06-06
That's helped, although for my test system I'm getting a limited amount of information. Anywhere else you might recommend looking?

---

### Post by sdennie on 2008-06-06
There will be things that only graphics card specific tools will be able to give you but, if you really read through the Xorg log, you really can glean a huge amount of information.

---

### Post by pcman312 on 2008-06-06
I've done the following on the Xorg log:

*grep "X Driver" Xorg.0.log*
```
<nothing>
```

*grep "ATI" Xorg.0.log*
```
(--) PCI:*(1:5:0) ATI Technologies Inc unknown chipset (0x791f) rev 0, Mem @ 0xfa000000/25, 0xfddf0000/16, 0xfdc00000/20, I/O @ 0xee00/8
(II) VESA(0): VESA VBE OEM: ATI ATOMBIOS
(II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc.
(II) VESA(0): VESA VBE OEM: ATI ATOMBIOS
(II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc.
```

*grep "flgrx" Xorg.0.log*
```
<nothing>
```

I've done a couple variations on those two searches, as well as looking through the log manually, with not much information unfortunately. It's possible that there aren't drivers installed on the system, so I could be looking at a case of incomplete information, but I'd rather be sure of that before I give up.

Luckily I've been able to get all of the nVidia information I need from that and */proc/driver/nvidia/cards/0* so there aren't any necessities there.

---

### Post by sdennie on 2008-06-06
It looks like the ATI machine you are trying to get info out of isn't using an ATI driver but instead the generic "vesa" driver.

---

