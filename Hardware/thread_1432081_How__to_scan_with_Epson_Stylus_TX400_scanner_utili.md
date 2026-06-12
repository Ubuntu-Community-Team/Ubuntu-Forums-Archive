---
title: "How  to scan with Epson Stylus TX400 scanner utility in UBUNTU9.10"
date: 2010-03-17
forum: Hardware
---

### Post by eyeman303 on 2010-03-17
[SIZE=2]The Epson Stylus TX400 is a MFD. It's printer is instantly detected in Ubuntu9.10,but the scanner is not detected by Xsane Image scanner utility.I have a Pinnacle PCTV PCI card ,which gets detected as the scanner device and not the epson MFD.I cannot install driver Imagescan from AVASYS,as an error message appears " [/SIZE]                                  [SIZE=2]Error: Dependency is not satisfiable: libltdl3 (>= 1.5.2-2)" How to solve this issue?[/SIZE]

---

### Post by ellgor on 2010-03-17
Hi,

Check in synaptic to see if libxsane-dev is installed, if not do so, if that doesn't get it working open a terminal and type in :

sudo xsane

ignore the warning and continue, seems to be a permission issue and this got my Epson SX115 recognised and xsane running. If you want that dependancy for iscan, go to Debian packages, look in the Lenny section-Old libs if not there try a newer release.(Squeeze - Sid!)

Regards, Ellgor.

---

### Post by eyeman303 on 2010-03-17
Hi **Ellgor**
    I installed the libxsane-dev via synaptic,and used the command sudo xsane.However xsane still fails to detect the epson tx400 scanner.I haven’t yet found the dependency for iscan. Thanks for your suggestion.
    Regards 
    eyeman303

---

### Post by eyeman303 on 2010-03-18
[LEFT]                                                                                Persistent problem
     [/LEFT]

---

### Post by eyeman303 on 2010-03-18
I installed **iscan** successfully after satisfying the dependencies. I ran the command **sudo xsane**
    [LEFT]after rebooting ,but still the epson stylus TX400 scanner is recognised. It picks up my Pinnacle PCTV internal card as the scanner device.On loading the device setting under preferences in the Xsane programme, it points to a file named     **Noname:PPinnaclePCTVStereo(saa7134).drc**.There is no file related to epson. How to proceed now?[/LEFT]

---

### Post by ellgor on 2010-03-18
Hi again,

Are you opening Imagescan up with its own launcher, its under Applications-Graphics-Image Scan probably with no icon as such, usually launches no problem.

Regards, Ellgor.

---

### Post by eyeman303 on 2010-03-18
Hi Ellger,
    [LEFT]My problem is solved.I’M SO HAPPY!:grin:[/LEFT]
    [LEFT]I reinstalled the latest version of iscan and started the program .Still it won’t find the scanner. Next I removed the usb connector of my Epson MFD to a different port and voila!, iscan detects the epson scanner. Xsane too detects the scanner.Thank you so much for all your time and guidance .:KS[/LEFT]
    [LEFT]Regards [/LEFT]
    [LEFT]eyeman303[/LEFT]

---

