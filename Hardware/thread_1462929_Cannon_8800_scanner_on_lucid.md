---
title: "Cannon 8800 scanner on lucid"
date: 2010-04-26
forum: Hardware
---

### Post by Thystra on 2010-04-26
hey all trying to setup my Canon 8800 scanner on Lucid.  Updated to the new back end as they say they have support for it, but the scanner is not showing up.  Any help would be appreciated.

```
alan@wyrm:~/Downloads/sane-backends-1.0.21$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
alan@wyrm:~/Downloads/sane-backends-1.0.21$ 

``````
alan@wyrm:~/Downloads/sane-backends-1.0.21$ sudo scanimage -L
[sudo] password for alan: 

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
alan@wyrm:~/Downloads/sane-backends-1.0.21$ 
``````
alan@wyrm:~/Downloads/sane-backends-1.0.21$ sudo sane-find-scanner 

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04a9 [Canon], product=0x1901 [CanoScan]) at libusb:001:004
found USB scanner (vendor=0x1737 [Cisco-Linksys LLC], product=0x0071 [Dual-Band Wireless-N USB Network Adapter]) at libusb:001:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
``````
alan@wyrm:~/Downloads/sane-backends-1.0.21$ scanimage -V
scanimage (sane-backends) 1.0.21; backend version 1.0.20
``````

alan@wyrm:~/Downloads/sane-backends-1.0.21$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:0745 Microsoft Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 084: ID 050d:0815 Belkin Components Nostromo n52 HID SpeedPad Mouse Wheel
Bus 001 Device 010: ID 046d:0a01 Logitech, Inc. USB Headset
Bus 001 Device 008: ID 046d:0990 Logitech, Inc. QuickCam Pro 9000
Bus 001 Device 007: ID 076b:3021 OmniKey AG CardMan 3121
Bus 001 Device 006: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 001 Device 004: ID 04a9:1901 Canon, Inc. 
Bus 001 Device 003: ID 1737:0071 Linksys 
Bus 001 Device 002: ID 050d:0237 Belkin Components F5U237 USB 2.0 7-Port Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by aikishugyo on 2010-05-08
Hi there,
I'm the person who submitted the patch to support the 8800F (with many thanks to several others of course, including the maintainer of the Pixma backend) so I can tell you the scanner is definitely supported.

scanimage -L does not find a scanner for several reasons. One may be that you need to be root (not sure about this), another that you have some information in /etc/sane.d/pixma.conf (or something like that) which overrides the new sane knowledge of USB IDs to scan for.

You can try to debug by setting to 255 the following environment variables:

SANE_DEBUG
SANE_DEBUG_PIXMA

and if you want more maybe

SANE_DEBUG_SANEI
SANE_DEBUG_DLL

There are others but these should suffice.

Best regards,
Gernot Hassenpflug

---

### Post by Thystra on 2010-05-08
Thanks for the input.  I went back and looked at things.  After make install with the source from sane backends apparently it didn't install the backends.  I had to manually update the pixma backend and now scanimage -L finds the scanner.  However, when I try to run XSane or Simple scan it doesn't detect the scanner / saying no source found.  

How do you tell the front ends to talk to the back ends that are found?

---

### Post by aikishugyo on 2010-05-09
> **Thystra said:**
> Thanks for the input.  I went back and looked at things.  After make install with the source from sane backends apparently it didn't install the backends.  I had to manually update the pixma backend and now scanimage -L finds the scanner.  However, when I try to run XSane or Simple scan it doesn't detect the scanner / saying no source found.

Hi,
Good news then! If scanimage -L finds the scanner, then that means the new backends are working. scanimage is a front-end, and others should work the same way. I am disconcerted by your description of the installation above: "I had to manually update the pixma backend". That does not sound right and I cannot begin to guess what else might be odd to then give the following problem with xsane.

> **Thystra said:**
> How do you tell the front ends to talk to the back ends that are found?

You don't, The front-end simple shows what the backends expose to it. SANE scans all USB IDs that it knows about for each backend and when it finds matches it adds them to a list that your front-end then asks you to choose from.

I suggest you redo the SANE installation. Try:

BACKENDS=pixma ./configure   <= on one line, so only update pixma

make clean <= just in case something is stuffed from previous time

make

(as root) make install

If any of these steps does not work, you'll have to sort that out before going on to the next one. Let's see how it goes...

Cheers,
Gernot

---

### Post by Thystra on 2010-05-11
Thanks for the help! after the reinstall scanner is now working!

---

### Post by aikishugyo on 2010-05-11
:guitar: Nice!
"do ut des"

---

