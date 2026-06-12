---
title: "HP G4050 scanner install help"
date: 2010-09-07
forum: Hardware
---

### Post by jsmkbunch2000 on 2010-09-07
I've search forums and the last post indicated in 2007 that their wasn't a patch to install this at that time.  I went away from Ubuntu because of stuff like this for about 2 years and thought I'd give it a try again.  I installed Ubuntu 10.04, and everything seems to work great, however I need my scanner HP G4050 to work.  I assume that since the last request was in 2007, and here we are in September 2010, that by now there is a Linux patch to get this scanner working???  Please help.

---

### Post by datacrusher on 2010-10-28
$lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 03f0:4605 Hewlett-Packard ScanJet G4050
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


I got the scanner listed, but xsane cant find it, or simple scanner. Any clues?

---

### Post by jsmkbunch2000 on 2010-11-04
bump

---

### Post by IcarusR on 2010-11-05
Scanjet G4050 is not supported by the current stable version of SANE
From [stable SANE supported devices web page]("http://www.sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD")...

> ScanJet G4050 	USB 	0x03f0/0x4605 	Unsupported 	Probably not supported. See link for details. 	unsupported
(2008-01-18 ) 	?

But has basic functionality in the SANE Development (git) Version
From [development git SANE supported devices web page]("http://www.sane-project.org/lists/sane-mfgs-cvs.html#Z-HEWLETT-PACKARD")

> ScanJet G4050 	USB 	0x03f0/0x4605 	Basic 	resolution from 100 to 600 supported, 1200 and 2400 remain to be added 	genesys
(1.0-8 ) 	sane-genesys

So to get this to work it looks like you will have to install the development git version of SANE.

---

### Post by jsmkbunch2000 on 2011-01-05
how do i do that?

---

### Post by IcarusR on 2011-01-06
Install git then in a terminal

```
cd ~/src
``` or whereever you want to do your work with CVS SANE
```
git clone git://git.debian.org/sane/sane-backends.git
cd sane-backends
```
```
BACKENDS=genesys ./configure
``` if you only want to build gensys backend (for this scanner), otherwise leave this line out

```
make
sudo make install
```

Never done this but I believe it should work.

---

### Post by gevan on 2011-02-15
To IcarusR: Thanks for the pointer. I had given up hope... I own the scanner since 2008.

I compiled the git version of sane and the scanner worked for the first time in Linux (Debian). Well, the functionality is minimal - gamma, brightness and contrast adjustments appear funtional but they do not work. Scanned images are slightly dark, but one can post-process them with acceptable results.

-Georgios

---

