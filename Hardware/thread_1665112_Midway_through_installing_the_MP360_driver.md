---
title: "Midway through installing the MP360 driver"
date: 2011-01-11
forum: Hardware
---

### Post by xtheunknown0 on 2011-01-11
I'm trying to install the driver for the Canon imageCLASS MP360.

I downloaded [http://home.arcor.de/wittawat/pixma/mp150-0.13.1.tar.bz2](http://home.arcor.de/wittawat/pixma/mp150-0.13.1.tar.bz2) and I'm in the middle of a sudo make install:

Please connect and turn on your scanner! I will try to detect it.
Please wait until your scanner is ready, then press return...read: 39: arg count
Connected scanner(s):
1: Canon SmartBase MP360 (SN:04A9263C_A03TWU)

I'm about to do a test scan. Please put a magazine or photo in the scanner.
The image will be saved in /tmp/pixmascan.pnm, log file in /tmp/pixmascan.log.
Proceed? [YES/no] YES
Executing: ./scan -x 10 -y 15 -w 51 -h 25 -1 -d 10 -W /tmp/pixmascan.pnm 2> /tmp/pixmascan.log
Connected scanner(s):
1: Canon SmartBase MP360 (SN:04A9263C_A03TWU)
Scan mode: color
DPI:       75x75
Offset:    (30,44) = (1.02cm, 1.49cm)
Dimension: 151x74 = 5.11cm x 2.51cm
Size:      33 kiB (uncompressed, raw)
Source:    Flatbed
Scanning...
100% done (33744 bytes written) 
Ok, the driver seems to work with your scanner.
Please check /tmp/pixmascan.pnm if it shows a small picture.

Install the stand-alone program in '/usr/local/bin'? [YES/no]

I realise that 5.11cm x 2.51 cm is tiny and is what I get at /tmp/ixmascan.pnm, but I've read in another ubuntuforum post that the poster could only scan tiny, top-quarter images - should I say YES? If I get the same problem as that poster, what do I do about it?; I know he didn't get help with this problem on that thread.

TIA,
xtheunknown0

---

### Post by xtheunknown0 on 2011-01-11
Since this is a relatively low activity section of ubuntuforums, I've decided to hit no for the time being. The output was then:

SANE backend directory: NOT FOUND!
SANE dll.conf: /etc/sane.d/dll.conf
Unable to find SANE backend directory and dll.conf!
Have you already installed the SANE package?

Why does this pop up?

TIA,
xtheunknown0

---

### Post by xtheunknown0 on 2011-01-15
bump

---

### Post by xtheunknown0 on 2011-01-16
bump

---

### Post by xtheunknown0 on 2011-01-20
bump

---

### Post by xtheunknown0 on 2011-01-21
bump

---

