---
title: "Vuescan can't see Fujitsu ix500 scanner on HP Elitebook?"
date: 2017-10-08
forum: Hardware
---

### Post by bbneo on 2017-10-08
I  am recently using a several year old (i7) HP Elitebook which dual boots  Windows 10 and Ubuntu Linux.  This machine has a fingerprint sensor  that I don't use, and it looks like maybe the "sane" drivers might be  seeing the fingerprint sensor as a scanner, but missing the Fujitsu  ix500 ScanSnap scanner although the scanner does show up in the "lsusb"  list.  

Vuescan DOES see the scanner when run under Windows 10 on this machine.  

I will attach my "lsusb" output and the vuescan log.

lsusb output:


```
"brad@brad-EB8460p:~$ lsusb
Bus 002 Device 004: ID 03f0:231d Hewlett-Packard Broadcom 2070 Bluetooth Combo
Bus 002 Device 003: ID 1bcf:2805 Sunplus Innovation Technology Inc. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 003 Device 002: ID 04c5:132b Fujitsu, Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 138a:003c Validity Sensors, Inc. VFS471 Fingerprint Reader
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



brad@brad-EB8460p:~$ sudo sane-find-scanner
[sudo] password for brad: 

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x138a, product=0x003c) at libusb:001:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
brad@brad-EB8460p:~$ 
"&#8203;


```

Any advice or suggestions?  Vuescan and this ix500 scanner are a "killer app" in my home office.

---

### Post by pdc on 2017-10-08
> Vuescan can't see Fujitsu ix500 scanner

........ **talk directly to VueScan** ......... always keen to help ......... [https://www.hamrick.com/support/](https://www.hamrick.com/support/)        email link on this page

They believe your device is fully supported: 

[https://www.hamrick.com/vuescan/fujitsu_scansnap_ix500.html#technical-information](https://www.hamrick.com/vuescan/fujitsu_scansnap_ix500.html#technical-information)

---

### Post by JoachimDurchholz on 2018-01-03
Sorry for answering so late - just accidentally hit this thread.
I know of two ways how the scanner might not be recognized:
- IIRC the SANE setup in Ubuntu 16 (LTS) is flaky. I upgraded to Ubuntu 17.04 and I got the scanner to work. Later I also installed the Fujitsu driver at [http://www.fujitsu.com/global/support/products/computing/peripheral/scanners/sp/software/ubuntu.html](http://www.fujitsu.com/global/support/products/computing/peripheral/scanners/sp/software/ubuntu.html) (Google told me about it, it's not directly reachable by navigation), so maybe that would work in isolation. I hear that this particular issue affects only USB 3.0 ports (which is unlikely to affect you but you should probably check), so YMMV.
- The scanner won't be found if you have any SANE-using software open - it seems that a scanner device can only be opened once at a time. Or maybe that's a specific of the ix500 software, or driver. Anyway, closing SimpleScan before doing the `scanimage -L` command would actually list the scanner for me. Of course this may or may not be your problem.

You are probably right about the fingerprint sensor, as vendor id and device id match the lsusb line for the Fingerprint Scanner.
My `scanimage -L` looks like this:
`found USB scanner (vendor=0x04c5 [Fujitsu], product=0x132b [ScanSnap iX500]) at libusb:001:041`

HTH, for what it's worth.

---

