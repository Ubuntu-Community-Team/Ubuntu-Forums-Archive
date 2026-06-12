---
title: "boot failure."
date: 2010-06-19
forum: Hardware
---

### Post by victorfuts on 2010-06-19
my system does not boot, it stucks after this line:

```
syscall_call +0x7/0xb
```

also tried re-installing ubuntu, this error even occurs just after a new installation.

is there anything to do with the graphic driver? or xconfig file? or hardware failure?

---

### Post by IcarusR on 2010-06-20
Did you do md5sum check on the downloaded iso ?
Does cd install OK on another box ?
Does live cd run on this box ?
How much ram do you have ? (seen similar issues with 4GB ram)

Suggest re-download iso, md5sum check it & burn at SLOW speed ie 6x.

Don't think graphics driver is loaded at this point.

---

### Post by victorfuts on 2010-06-20
> **IcarusR said:**
> Did you do md5sum check on the downloaded iso ?
Does cd install OK on another box ?
Does live cd run on this box ?
How much ram do you have ? (seen similar issues with 4GB ram)

Suggest re-download iso, md5sum check it & burn at SLOW speed ie 6x.

Don't think graphics driver is loaded at this point.

hi,

Thanks for the suggestions

installed on other computer with same iso and USB (i burned into an USB and verified with the burning tool). Live USB works perfect.

and YES! I DO HAVE 4G RAM. next time i'll try to unplugged one of the 2g memory and see if there's any further issue.

---

### Post by victorfuts on 2010-06-25
> **victorfuts said:**
> hi,

Thanks for the suggestions

installed on other computer with same iso and USB (i burned into an USB and verified with the burning tool). Live USB works perfect.

and YES! I DO HAVE 4G RAM. next time i'll try to unplugged one of the 2g memory and see if there's any further issue.


problem solved.

nothing to do with memory, graphics card, but i have a usb wifi device plugged into computer, seem there's driver problem with the wifi when loading kernel, now i always remove the wifi device when booting. and plug it back to computer after gdm starts.

---

