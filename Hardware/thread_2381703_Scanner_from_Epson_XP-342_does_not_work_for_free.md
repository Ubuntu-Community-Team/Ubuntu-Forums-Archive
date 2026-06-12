---
title: "Scanner from Epson XP-342 does not work for free"
date: 2018-01-04
forum: Hardware
---

### Post by Valentin630 on 2018-01-04
Standard Epson drivers were installed:
kuzmin@bel02:~$ scanimage -L
device `epson2:net:10.0.2.82' is a Epson PID 1115 flatbed scanner
device `imagescan:esci:usb:/sys/devices/pci0000:00/0000:00:13.4/usb6/6-2/6-2:1.0' is a EPSON XP-342_343_345_Series 

ImageScan sees only  USB scanner and can do only Preview. The program offers to
scan in a file and does not create the file.

Xsane sees  both scanners but its result is random points.

VueScan works OK, but includes in the image its wattermarks,  demanding $20 for their disappering
in the home version.

SimpleScan tries to do something, but the result is wight field.

Can somebody comment the situation - is it hopelessly to do not pay?

---

### Post by him610 on 2018-01-04
The Epson XP-342 is an inkjet multifunction device, is it not? 
Does it perform all of its other functions - print, copy, fax, and scan (from the device itself)? sometimes the inkjets clog and dry up.
What version of ?buntu are you using?

Don't know if I can help or not, but maybe some of these suggestions will work for you.
You might consider disconnecting one scanner until you get the remaining connected scanner working satisfactorily.

I have one Brother network multi-function device installed, and one Epson USB flatbed installed. Using LTS 16.04.03, both are operational using Image Scan for the Epson USB flatbed, and Simple Scan for the Brother MFC network scanner.
Unfamiliar with Vuescan, do not have Xsane installed, so I can not comment on those.

> ImageScan sees only USB scanner and can do only Preview
This may be the result of the original setup. If you can preview the document you should be able to print it out to a *png* file using Image Scan (you won't be concerned with poor printer output or wasted ink). 
You may need to turn off one scanner, and power cycle the other one. The network scanner may be in a power-save condition - not responding to polls.
Use only one scanner application at the same time.

---

### Post by Valentin630 on 2018-01-05
Thanks, I understand that I have only one device. The system is 16.04-3
> **him610 said:**
> If you can preview the document you should be able to print it out 
By my opinion: nobody should, the software can if it was written by right guys.
I suspect, that nobody checked drivers in 16.04. The absence of the XP-342 support in Xsane
points to this fact. My question is more about: does anybody has an experience with XP-342 in 16.04?

---

### Post by sccman on 2018-01-05
I would agree that there shouldn't be any reason you need to pay for software when you have free and open source software. 

It looks like Ubuntu has the capability to detect and use the scanners if VueScan works. Plus given that VueScan works and the other applications don't work, it's possibly a configuration error or that the software doesn't support your printer yet.

We'll need more information on problems with the applications:
1) On Xsane, what do you mean by "random points?" Could you describe what that looks like?
2) On SimpleScan, what is happening? What is going wrong?

---

### Post by pqwoerituytrueiwoq on 2018-01-05
I did make a web UI for scanimage (link in signature)
if scanimage can scan it it will work
if you post the output of scanimage --help i can give you a command to use as a test to see if it works

---

### Post by Valentin630 on 2018-01-06
> **sccman said:**
> 
We'll need more information on problems with the applications:
1) On Xsane, what do you mean by "random points?" Could you describe what that looks like?
2) On SimpleScan, what is happening? What is going wrong?



xsane    [https://youtu.be/Er9sx0IFl2E](https://youtu.be/Er9sx0IFl2E)

I am sorry about the SimpleScan. It works by network! It does not work by USB.
simplescan    [https://youtu.be/OahqQtHudss](https://youtu.be/OahqQtHudss)

And ImageScan by Epson
[https://youtu.be/nVi4I2SyKtM](https://youtu.be/nVi4I2SyKtM)

---

### Post by sccman on 2018-01-09
On Xsane, what do you mean by "random points" though? I need help in understanding what the problem is.

---

