---
title: "Wacom xmax value is wrong"
date: 2007-01-11
forum: Hardware &amp; Laptops
---

### Post by DoctorMO on 2007-01-11
Hi all, still not having ANY joy with this Intuos tablet, I changed the mice to mouse1 in the xorg pointer config as shown in the HOWTO but now the tablet doesn't do anything at all.

I think the tablet is being taken over by the standard mouse hid and the wacom kernel module doesn't get a chance to insert it's self correctly.

Are the ways I can check this? is there anything I can do to test whats going wrong?

The only 'errors' I get in the xorg.conf are:

WACOM: xmax value is wrong
WACOM: xmax value is wrong

which doesn't mean a great deal to me.

---

### Post by graigsmith on 2007-01-12
have you tried following the howto? 

also it helps to install the package wacom-tools.  this makes a driver you can link to called wacom.

---

### Post by DoctorMO on 2007-01-12
followed the Howto to the letter, and since it says to install wacom-tools you betcha their installed too.

---

### Post by DoctorMO on 2007-01-12
OK the problem is that the wacom kernel module doesn't list my tablet, it is supported just not in this version. so it's being stolen by usbhid instead.

Drat it I'll have to recompile the kernel: NOT what I wanted to do considering how difficult that is to do with ubuntu.

---

