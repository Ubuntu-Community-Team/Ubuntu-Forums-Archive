---
title: "simple scan does not find scanner"
date: 2020-10-13
forum: Hardware
---

### Post by s9032g@comcast.net on 2020-10-13
Ubuntu 20.04. Canon Pixma TS9120  Dell Latitude e7240. Printer connected by usb

Scanner works with other laptops. Turned on, Restarted,  Suspect that I need to uninstall or install some files??

---

### Post by Dennis N on 2020-10-13
I had this error not long ago when resurrecting an Acer scanner which was last used with Windows XP 15 years ago.
The terminal can help by giving some feedback on the problem:

Can sane see the scanner?
```
sane-find-scanner
```
If not found, be sure scanner is on. Try again with sudo. Other suggestions I have seen are: try another USB port. Try another cable. 
Check to be sure scanner is supported: [http://www.sane-project.org/sane-supported-devices.html](http://www.sane-project.org/sane-supported-devices.html)
If found (my Acer was found), try the command:
```
simple scan
```
It may point to the problem, similar to this:
```
dmn@Sydney:~$ simple-scan
[snapscan] download_firmware: No firmware entry found in config file snapscan.conf.
```
Following that message, there were instructions on how to setup firmware. Firmware here means driver. For mine, not only was there no firmware entry in the config file, there was no driver. You need a specific driver for your scanner model. Find it online if you don't have it on some driver disk and copy it to the right location, then edit the config file probably in /etc/sane.d. Then it should work.

---

### Post by s9032g@comcast.net on 2020-10-13
Thanks. Commands tell me scanner is not detected. The SANE site tells me that whatever they have for my scanner is "untested". They need testers. I am not anxious to be a tester.

If I find a solution I will post it.

---

### Post by SeijiSensei on 2020-10-13
See if VueScan works with it:  [https://www.hamrick.com/linux-scanner-software.html](https://www.hamrick.com/linux-scanner-software.html)

---

