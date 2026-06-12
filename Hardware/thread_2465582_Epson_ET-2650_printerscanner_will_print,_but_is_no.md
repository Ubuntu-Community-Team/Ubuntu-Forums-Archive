---
title: "Epson ET-2650 printer/scanner will print, but is not found for scanning"
date: 2021-08-05
forum: Hardware
---

### Post by John Nagle on 2021-08-05
I recently converted a desktop machine from Ubuntu 16.04 LTS to 20.04 LTS.

Previously, the USB-connected ET-2650 printer/scanner would print with normal printing, and would scan with XSane.

Now, under 20.04 LTS, printing still works, but XSane and SimpleScan cannot find the scanner.

Xsane version: 0.999-8ubuntu2.1
libsane version: 1.0.29-0ubuntu5.2

Synaptic Package Manager says these are the latest versions.

The SANE web site lists support for this scanner as "good", and the backend required is:

[TABLE]
[TR]
[TD][/TD]
[TD="align: center"] epson2
(1.0.124 (unmaintained))[/TD]
[TD="align: center"][sane-epson2]("http://sane-project.org/man/sane-epson2.5.html")[/TD]
[/TR]
[/TABLE]

What I have seems to be "libsane-epson2.so.1.0.29", which is what Ubuntu gave me. Is Ubuntu way, way behind, or what?

It all worked back in 16.04 LTS.

---

### Post by linuux on 2021-08-06
Is there any Epson ET-2650 series packages (printer driver) installed - check Synaptic Package Manager?   What's the scanner driver version at?   It should be at version 3.65.0, minimum.   

[https://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](https://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)

Enter ET-2650.

Cross match the info there with what Ubuntu installed or has available for install.

---

