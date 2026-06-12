---
title: "HP scanner not working after 17.10 upgrade"
date: 2017-10-30
forum: Hardware
---

### Post by Daniel_Rosehill on 2017-10-30
Hi,

Upgraded from 17.04 to 17.10 last night and have just noticed that the scanner on my HP 1510 (combo printer/scanner) is no longer recognizing.

Output from sane-find-scanner is:


```


  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.


  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.


could not open USB device 0x1d6b/0x0003 at 002:001: Access denied (insufficient permissions)
could not open USB device 0x046d/0xc534 at 001:012: Access denied (insufficient permissions)
could not open USB device 0x046d/0xc31c at 001:008: Access denied (insufficient permissions)
found USB scanner (vendor=0x03f0 [HP], product=0xc111 [Deskjet 1510 series]) at libusb:001:013
could not open USB device 0x046d/0x0a38 at 001:010: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 001:001: Access denied (insufficient permissions)
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.


  # Not checking for parallel port scanners.


  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.


  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.



```

How do I begin troubleshooting this?

Have already tried reinstalling HPLIP, running xscan as sudo and no improvement. By the way, the printing is working perfectly so only the scanner seems to be affected.

---

### Post by pdc on 2017-10-30
sorry to hear of your problems; perhaps you start here [https://help.ubuntu.com/community/ScanningHowTo#A.22No_device_available.22_-_what_to_do.3F](https://help.ubuntu.com/community/ScanningHowTo#A.22No_device_available.22_-_what_to_do.3F) 

17.10 is seen by some as experimental: ..... trying out the new; creating traps that folks fall into; and over time may get fixed; I have heard it suggested there should be a health warning on "upgrade to 17.10" 

The distro Mint sticks to the LTS versions of Ubuntu only: they are at 16.04 and next big change will be about June 2018 when Mint 19 gets released;

folks are reporting issues with the Canon UFR driver; (Canon released an update in July); 

The Ubuntu download page starts with LTS I see [https://www.ubuntu.com/download/desktop](https://www.ubuntu.com/download/desktop)

---

### Post by gina.R on 2017-11-18
I have the same problem after upgrade 17.04 to 17.10. I have a Lexmark printer/scanner.  I get the same output from sane-find-scanner. I have followed suggestions from various sites, but scanner still not found.

---

### Post by alexsmith on 2017-11-22
This worked for me:

[https://help.ubuntu.com/community/HpAllInOne](https://help.ubuntu.com/community/HpAllInOne)

Basically, I had to reconfigure the printer using:

```
hp-setup
```

Then I was able to scan a page using:

```
hp-scan
```

I then also tested ```
simple-scan
``` and it worked.

Hope that helps.

---

### Post by Geoffrey_Arndt on 2017-11-22
Duplicate comment - - deleted.

---

### Post by hunterkasy on 2017-11-22
> **alexsmith said:**
> This worked for me:

[https://help.ubuntu.com/community/HpAllInOne](https://help.ubuntu.com/community/HpAllInOne)

Basically, I had to reconfigure the printer using:

```
hp-setup
```

Then I was able to scan a page using:

```
hp-scan
```

I then also tested ```
simple-scan
``` and it worked.

Hope that helps.

Thank you, this made my scanner work again after I upgraded to 17.10

---

