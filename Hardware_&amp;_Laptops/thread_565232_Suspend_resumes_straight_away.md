---
title: "Suspend resumes straight away"
date: 2007-10-02
forum: Hardware &amp; Laptops
---

### Post by Sarke on 2007-10-02
Hi, I tried searching, but I couldn't find anything.

My problem is that when I go to suspend (or hibernate for that matter), it powers everything down ok, but it turns right back on straight away.  Everything works fine after coming back on, but it's the "not staying suspended" part that's the problem.

My guess is that there's a device that wakes the computer up straight away, and if I had to guess it would be the onboard network card (but again, that's just a guess).  My mobo is a ASUS P5P800-MX.  Devices connected are nothing special (USB hub, mouse, keyboard, monitor).  My video card is an nVidia 7800 GS running the binary restricted drivers (whatever is the normal).

I can get this info from acpitool, but I don't really know what else to do...

```
~$ acpitool -e
  Kernel version : 2.6.20-16-gener20060707   -    ACPI version : 20060707
  -----------------------------------------------------------
  Battery status : <not available>

  AC adapter     : <not available>
  Fan            : <not available>

  CPU type               : Intel(R) Pentium(R) 4 CPU 2.40GHz 
  CPU speed              : 2398.930 MHz 
  Cache size             : 512 KB
  Bogomips               : 4801.71 
  Bogomips               : 4798.06 

  # of CPU's found       : 2

  Processor ID           : 0
  Bus mastering control  : no
  Power management       : no
  Throttling control     : no
  Limit interface        : no
  Active C-state         : C0
  C-states (incl. C0)    : 1

  Processor ID           : 1
  Bus mastering control  : no
  Power management       : no
  Throttling control     : no
  Limit interface        : no
  Active C-state         : C0
  C-states (incl. C0)    : 1


  Thermal info   : <not available>

   Device       Sleep state     Status
  ---------------------------------------
  1. P0P4          4            disabled
  2. MC97          4            disabled
  3. USB1          4            disabled
  4. USB2          4            disabled
  5. USB3          4            disabled
  6. USB4          4            disabled
  7. EUSB          4            disabled
  8. ILAN          4            disabled

```

Thanks.

---

### Post by nick_h on 2007-10-02
Have a look at the [HowTo: Debug Suspend, Resume, Hibernate issues](http://ubuntuforums.org/showthread.php?t=505890) thread.

I suspect that something is stopping it suspend properly. Section 4 about putting a "set -x" in the sleep script may be helpful.  Also have a look in your kernel log files.

---

### Post by Rob500 on 2007-10-02
You don't have anything in the BIOS enabled such as wake on LAN by any chance do you?

---

