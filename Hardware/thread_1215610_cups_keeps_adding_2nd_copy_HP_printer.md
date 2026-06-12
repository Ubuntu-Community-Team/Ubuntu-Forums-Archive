---
title: "cups keeps adding 2nd copy HP printer"
date: 2009-07-17
forum: Hardware
---

### Post by gwoodruff on 2009-07-17
Howdy all, I have 64 bit 9.04  and a HP6300 officejet that has functioned fine all the way back to 6.06. I have upgraded to 9.04 and am pulling my hair out! When I delete all copies of the printer and let it discover it adds the following printer:

hp:/usb/Officejet_6300_series?serial=CN687CG30Z04J5

I can print and everything is fine. Then cups? will detect and add a second copy:

hal:///org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_02_1_if1_printer_CN687CG30Z04J5

 Cups? dis-ables the first printer and I cannot print. if I remove the 2nd printer and re-enable the first I can print. The second printer will re-appear within a few minutes.

HELP!!!!
Gary

---

### Post by gwoodruff on 2009-07-20
bump,  pls help

Gary

---

### Post by gwoodruff on 2009-07-21
I have found a way to bypass the error and get printing. I removed the usb cable and configured the printer a a network printer. I can now print! I believe printing is an issue in jaunty. I find MANY posts from people who have printed fine for the last few releases and are now having problems. This needs to be addressed as if we cant have reliable printing Gates will always have the dominate os. I use ubuntu as my primary os for my business and did not like having to boot into windows to print.

Gary

---

### Post by MockY on 2009-07-29
I hear you. My HP LaserJet 1018 has worked for many releases, but even with manual installation, Jaunty simply refuses to print. While booting, half of the times, the boot stalls on USB detection and wont continue until I unplug the printer. So yes, something is very wrong with how printing is handled in Jaunty. Luckily, I have a LaserJet 1020 as well, and that one works with no problems.

---

