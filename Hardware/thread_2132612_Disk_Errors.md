---
title: "Disk Errors"
date: 2013-04-05
forum: Hardware
---

### Post by Joseph Wraith on 2013-04-05
Hello,

I'm getting some very annoying errors:

1. DISK FAILURE IS IMMINENT.
2. Realocated Sector Count.


It would be great if someone could help!

Thanks in advance.

---

### Post by ibjsb4 on 2013-04-05
Not only annoying, but invisible :)

---

### Post by Joseph Wraith on 2013-04-05
I updated with Text :P

---

### Post by ibjsb4 on 2013-04-05
You should be able to check you disk drive with "Disk Utility".  You already have it installed.

---

### Post by Joseph Wraith on 2013-04-05
I did and it just throws these errors at me.

---

### Post by ibjsb4 on 2013-04-05
It should of given you a detailed report.  Lets try another route.  [Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo smartctl -i /dev/sda
```

Whats that give you?

---

### Post by Joseph Wraith on 2013-04-05
=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Scorpio Blue Serial ATA
Device Model:     WDC WD5000BEVT-22ZAT0
Serial Number:    WD-WXC0A79X2420
LU WWN Device Id: 5 0014ee 2587af3d0
Firmware Version: 01.01A01
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Fri Apr  5 16:09:45 2013 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

---

### Post by matt_symes on 2013-04-05
Hi

Before you do anything, backup any data (files) you cannot afford to lose to an external hard drive or cloud storage.

After that investigate any hard drive errors.

You can run a test with smartctl

```
sudo smartctl -t long /dev/sda
```

and then view the results after it has finished. It will take a while.

```
sudo smartctl -a /dev/sda
```

Before you do anything though: backup, backup, backup.

Kind regards

---

### Post by ahallubuntu on 2013-04-05
~

---

