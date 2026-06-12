---
title: "how to get Canon scanner 3200f working"
date: 2009-06-04
forum: Hardware
---

### Post by joehansen on 2009-06-04
Hi i'm on a Ubuntu 8.10 32

I have a Canon 3200f but don't know how to get it to work.

I have installed Xsane (it can't find the scanner).

joe@joe-desktop:~$ lsusb
Bus 005 Device 005: ID 04a9:2216 Canon, Inc. CanoScan 3200F
Bus 005 Device 002: ID 04a9:10a5 Canon, Inc. iP5200
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse
Bus 002 Device 004: ID 046d:c312 Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

and i found this on their homepage.

Backend     Version     Supported Devices     Manual Page             Manufacturer     Model     Interface     USB id     Status     Comment            Backends neither included in the current tarball nor the CVS repository   cs3200f  *none*  [Canon]("http://www.canon.com/")  [CanoScan 3200F]("http://www.sane-project.org/unsupported/canon-3200f.html") USB 0x04a9/0x2216  [COLOR=#b00000]minimal[/COLOR]   Backend is in experimental CVS.  


joe@joe-desktop:~$ sudo chmod 660 /proc/bus/usb/005/005
chmod: kan ikke tilgå '/proc/bus/usb/005/005': No such file or directory

---

### Post by jerrrys on 2009-06-05
[http://ubuntuforums.org/showthread.php?t=1143061](http://ubuntuforums.org/showthread.php?t=1143061)

---

### Post by Lauri Pirttiaho on 2010-03-03
There is no support for Canoscan 3200F in SANE, and likely will not
come in near future. 

Suggest getting a scanner that is supported in SANE (not one made
by Canon).

The experimental driver will not be continued until more information
becomes available from Canon and that looks unlikely at present.

-- Lauri

---

### Post by gacb on 2010-09-22
I gave up and bought a second-hand HP 2300C for $20.00. It's a flatbed that works perfectly with Lucid and Maverick, although the latter needs a few tweaks in gscan2pdf to run in all modes.

I also have an HP 4215 OfficeJet I use on the road. It's worked flawlessly since I started using Ubuntu three years ago.

---

