---
title: "Upgraded Kubuntu on 11/05/08 and EVDO card not working"
date: 2008-11-07
forum: Hardware
---

### Post by burtbick on 2008-11-07
FIXED: See 3rd reply post.

Hi,

I installed the latest upgrades to Kubuntu on Wed 11/05/08 and now my Verizon PC5750 EVDO card is not being recognized by KPPP.  It was working flawlessly for months, even through several upgrades including Kernels, etc.

KPPP finds the modem at ttyUSB0, and using dmesg I can see that is where the card is found when it is plugged in.

I do not find any reference to the card in proc/bus/usb (in fact nothing is present there even if I plug in my USB mouse, which does work).

How can I track down what has happened with this upgrade (note this was NOT a version upgrade, just upgraded the latest patches, etc. including the kernel.  The upgrade did include KDE so maybe something there borked KPPP but I'm thinking that it is more likely something with a kernel module somewhere.

Again the EVDO card had been working fine for months.

Since I haven't been able to locate the information about vendor ID, etc. that I see mentioned in some of the forum notes for using with modprobe I haven't been able to try that yet.  Also lsmod shows that usbserial is loaded with "airprime".

Thanks,
Burt

---

### Post by burtbick on 2008-11-07
OK, found lsusb.  That shows the EVDO card when it is plugged in, and dmesg shows when the card is ejected (disconnects from ttyUSB0...) and when the card is plugged in (connects to ttyUSB0..)  But with the card in KPPP still doesn't appear to be able to fully talk to it.  Knows it is there (if I try KPPP with the card out it definitely knows that it is not there).  but with the card in it is as described above.  I saw there was a new modules update for kubuntu and have installed that.  I'll try rebooting for good measure just in case that fixed the problem.

Thanks,
Burt

---

### Post by burtbick on 2008-11-07
Interesting.. Fixed the problem..

Previously I either had to use ttyUSB0 or ttyACM0 to talk to the EVDO card.  It has always been either of those depending on whether or not the USB wireless mouse was plugged in.

This time just for grins I tried ttyUSB1, ttyUSB2 with no luck.  But ttyUSB3 is working.

So if someone else runs into this problem try all of the possible ttyUSBnn (and maybe ACMnn ports).

Thanks,
Burt

---

