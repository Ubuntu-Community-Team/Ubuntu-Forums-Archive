---
title: "Lexmark X63 Scanner Not Detected"
date: 2009-08-10
forum: Hardware
---

### Post by johndoe32102002 on 2009-08-10
After a clean upgrade from Ubuntu 8.04 to Ubuntu 9.04, Ubuntu fails to detect my Lexmark X63.  I have SANE installed and even tried compiling the latest version.  My Lexmark X63 used to scan fine with Ubuntu 8.04, so I know my scanner is compatible with Ubuntu.

I need any suggestions in getting my X63 to scan.

Technical Details:

lsusb:
Bus XXX Device XXX: ID 043d:005a Lexmark International, Inc. X63

sane-find-scanner
# No USB scanners found.

scanimage -L
No scanners were identified.

Thanks,
John

---

### Post by stovicek on 2009-08-10
Someone asked about the X63 in regards to CUPS at Launchpad.
[https://answers.launchpad.net/ubuntu/+source/cups/+question/75766](https://answers.launchpad.net/ubuntu/+source/cups/+question/75766)

Maybe the solution, switching to the Z53 driver, is the same.
[http://leenooks.com/page/show/X63](http://leenooks.com/page/show/X63)

---

### Post by johndoe32102002 on 2009-08-10
I saw this thread, but I have no problem with the printer, which CUPS runs; I am having problems with the scanner on the device.  I believe this might be a SANE problem, except I compiled the newest version and it still didn't recognize the Lexmark X63 scanner.

---

### Post by IcarusR on 2009-08-11
Lexmark X63 is not mentioned on the 'supported devices page of Sane site, so it may not be supported (not work)
[http://www.sane-project.org/sane-mfgs.html#Z-LEXMARK]("http://www.sane-project.org/sane-mfgs.html#Z-LEXMARK")

---

