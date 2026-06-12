---
title: "using hp scanner which is not detected in 12.04"
date: 2013-02-17
forum: Hardware
---

### Post by jamesbon on 2013-02-17
I have a new scanner lsusb shows
> Bus 002 Device 003: ID 03f0:042a Hewlett-Packard
when I try to scan with simple scan I am unable to scan, it says
> "Failed to scan
unable to connect to scanner"

what should I check

---

### Post by pme 72 on 2013-02-17
Try looking at the man pages for sane. 

Open a terminal window and run ```
man sane
```

Scroll down to the Problems text. 

Downloading and installing the latest version of hplip from the HP website seemed to solve my issues but I had deleted a required file.

---

### Post by foresthill on 2013-02-17
The model of the HP scanner you're using would be helpful.

Install xsane either through Software Center, Synaptics or the terminal. Also install several of the scanning programs and try each of them. Also, installing HPLIP couldn't hurt.

Simple scan is probably the worst of the lot and I'm not sure if xsane is even installed along with it.

I had an HP scanner a few years ago that would not work. Spent many weeks trying to get it to work, but no luck, it flat out wasn't supported.

Finally, if you can't get it to work, check your local thrift store. They often have piles of scanners for very cheap, ~ $5.00 or so. Canon LIDE scanners are my favorite because they have great support and don't even require an AC adapter. 

HTH and good luck.

---

### Post by jamesbon on 2013-02-21
> **foresthill said:**
> The model of the HP scanner you're using would be helpful.

Laser Jet M1136 MFP is model of scanner.

---

### Post by foresthill on 2013-02-21
The fact it's a multi-function unit reduces the chances it will be supported.

I just looked over the list of drivers for HP printers and didn't see your model listed, though a few of the multi-function ones supposedly are, just not yours. Sometimes a driver for a similar model will work, but good luck on this.

---

### Post by MikRose on 2013-08-06
Hi, just noticed your response mentioning LIDE Canon scanner.  I have a Canon LIDE 20 that was working fine on many Linux distros, most recently 12.04 for about a year.  
Now Simple Scan soesn't recognize the scanner.  
Scanner Utility will recognize the scanner, but I can't get the settings adjusted to use it easily like Simple Scan did.  
Frustrating.

---

### Post by linuxonbute on 2013-08-07
Not that it's of much help to you perhaps but look on HP's site as I have always found they give very good support for Linux.
I have had a PSC1205 ( this is multifunction ) I now have a networked Officejet  6500 E710a-f ( again multifunction ) and i have a HP G56 laptop. They all have worked fully but for the PSC1205 I needed to get the help from the HP site.

---

