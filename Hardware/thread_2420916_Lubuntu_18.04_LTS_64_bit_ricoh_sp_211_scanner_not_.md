---
title: "Lubuntu 18.04 LTS 64 bit: ricoh sp 211 scanner not working"
date: 2019-06-13
forum: Hardware
---

### Post by erotavlas on 2019-06-13
Hi,
I installed Lubuntu 18.04 LTS 64 bit instead of windows 7 on an old PC. I have a problem with multifunction printer-scanner ricoh sp 211 su. On the ricoh Web site [ there are not drivers]("http://support.ricoh.com/bb/html/dr_ut_e/re1/model/sp211su/sp211su.htm"), but I have installed[ the drivers for the higher model]("http://support.ricoh.com/bb/html/dr_ut_e/apc/model/sp221/sp221.htm") (printer and scanner).
The printer is detected and it works after that I installed it by adding a printer with a generic driver.
The scanner does not work and both xsane and simple-scan do not detect it. I tried as described in other discussions:
The device is detected as stated by lusb
```
lsusb
Bus 002 Device 002: ID 058f:a001 Alcor Micro Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05ca:044f Ricoh Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
but not by scanimage
```
scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
```

While it is detected by sane-find-scanner
```
sudo sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x05ca [RICOH ], product=0x044f [RICOH SP 211SU]) at libusb:001:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

```

I added the user to the groups:
```
sudo adduser $USER scanner
sudo adduser $USER saned
```
and
```
groups
user adm cdrom sudo dip plugdev lpadmin scanner sambashare saned
```

Thank you in advance.

---

### Post by brian_p on 2019-06-13
Lots of nice detail. The scanimage output tells you that SANE cannot find a backend (driver) for the scanner.

> **erotavlas said:**
> 

[...]

I added the user to the groups:
```
sudo adduser $USER scanner
sudo adduser $USER saned
```


This doesn't do any good and isn't needed (even if a backend was found).

r78182en.exe contains sp-200-series-gdi-1.01-i386.deb. There is software in the Debian file for the printer, but none for the scanner.

---

### Post by erotavlas on 2019-06-13
> **brian_p said:**
> Lots of nice detail. The scanimage output tells you that SANE cannot find a backend (driver) for the scanner.



This doesn't do any good and isn't needed (even if a backend was found).

r78182en.exe contains sp-200-series-gdi-1.01-i386.deb. There is software in the Debian file for the printer, but none for the scanner.

[r78188en.exe]("http://support.ricoh.com/bb/html/dr_ut_e/apc/model/sp221/sp221.htm") is Linux SANE Scanner Driver that contains sp-200series_Scanner-1.01-noarch. I installed it, but it does not work. The scanner is detected the problem is on the backend. What do you suggest to do?

---

### Post by brian_p on 2019-06-13
> **erotavlas said:**
> [r78188en.exe]("http://support.ricoh.com/bb/html/dr_ut_e/apc/model/sp221/sp221.htm") is Linux SANE Scanner Driver that contains sp-200series_Scanner-1.01-noarch. I installed it, but it does not work. The scanner is detected the problem is on the backend. What do you suggest to do?

Please read

[https://wiki.debian.org/Scanner#issue](https://wiki.debian.org/Scanner#issue)

The Ricoh Debian package has the backend (libsane-sp_200series.so.1.01.0) in */usr/lib/sane*. Copying (or linking) this file to the correct place could be a full solution.

---

### Post by brian_p on 2019-06-14
Solved?

---

### Post by erotavlas on 2019-06-15
> **brian_p said:**
> Please read

[https://wiki.debian.org/Scanner#issue](https://wiki.debian.org/Scanner#issue)

The Ricoh Debian package has the backend (libsane-sp_200series.so.1.01.0) in */usr/lib/sane*. Copying (or linking) this file to the correct place could be a full solution.

I did not solve. I copied libsane-sp_200series.so.1.01.0 from /usr/lib/sane to both /usr/lib/x86_64-linux-gnu/sane/ and /usr/lib/i386-linux-gnu/sane/, then I restarted the system, but both xsane and simple-scan do not detect it.

---

### Post by brian_p on 2019-06-15
> **erotavlas said:**
> I did not solve. I copied libsane-sp_200series.so.1.01.0 from /usr/lib/sane to both /usr/lib/x86_64-linux-gnu/sane/ and /usr/lib/i386-linux-gnu/sane/, then I restarted the system, but both xsane and simple-scan do not detect it.

I wonder whether it would be better to delete the copied files and make links to libsane-sp_200series.so.1.01.0 from /usr/lib/x86_64-linux-gnu/sane/ and /usr/lib/i386-linux-gnu/sane/?. Perhaps libsane-sp_200series.so.1.01.0 looks for other files in the installed package.

---

### Post by erotavlas on 2019-06-29
> **brian_p said:**
> I wonder whether it would be better to delete the copied files and make links to libsane-sp_200series.so.1.01.0 from /usr/lib/x86_64-linux-gnu/sane/ and /usr/lib/i386-linux-gnu/sane/?. Perhaps libsane-sp_200series.so.1.01.0 looks for other files in the installed package.

I deleted the files from the two folders and I made a two symbolic links. Unfortunately, nothing changed.

---

### Post by erotavlas on 2019-07-05
Well, I resign myself to telling my friend that he can't use the scanner. Too bad for these problems that limit the spread of GNU/linux.

---

### Post by erotavlas on 2019-07-05
I found a solution. I will use scan to USB drive function and then I will connect it to the PC. It is not immediate, but works.

---

