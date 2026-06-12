---
title: "Trouble getting SANE Scanning working"
date: 2014-04-17
forum: Hardware
---

### Post by CybaCowboy on 2014-04-17
Okay,


I'm trying to get my HP Deskjet F380 All-in-One working with [Qoppa Software's]("http://www.qoppa.com") "[PDF Studio Pro]("http://www.qoppa.com/pdfstudio/")", which in turn requires my multi-function device to be configured via and for use with [SANE]("http://www.sane-project.org")...

I have followed the instructions here:
[https://help.ubuntu.com/community/sane.d%20tutorial](https://help.ubuntu.com/community/sane.d%20tutorial)

 But [PDF Studio Pro]("http://www.qoppa.com/pdfstudio/") tells me that "There are no [SANE]("http://www.sane-project.org") sources installed" when I try to scan something, and [Qoppa Software]("http://www.qoppa.com") insist that [SANE]("http://www.sane-project.org") has not been setup correctly (which in all honesty, is probably the case).. My multi-function is connected locally (via USB), and I can scan just fine with "Simple Scan" (which is a part of [SANE]("http://www.sane-project.org"), isn't it?).

Any help would be appreciated.

---

### Post by pdc on 2014-04-18
so simple scan is a frontend for SANE

[https://apps.ubuntu.com/cat/applications/simple-scan/](https://apps.ubuntu.com/cat/applications/simple-scan/)

paste this into a terminal > dpkg -l | grep sane and see if it lists various packages of sane; 

we still use synaptic as our package manager: if you click on your package manager, does it allow you to see what is installed?

this is what we have installed; see the enclosed thumbnail: perhaps you check on your system for what you have

do look for libsane-extras (it may be well down the list and right-click on its entry; select "mark for installation" and then go to TOP LINE of synaptic and click APPLY to install it and any others you need)

---

### Post by CybaCowboy on 2014-04-18
Yeah, I have plenty of entries for [SANE]("http://www.sane-project.org") shown:

```

ii  libsane:amd64                                               1.0.23-3ubuntu3                                     amd64        API library for scanners
ii  libsane:i386                                                1.0.23-3ubuntu3                                     i386         API library for scanners
ii  libsane-common                                              1.0.23-3ubuntu3                                     amd64        API library for scanners -- documentation and support files
ii  libsane-hpaio                                               3.14.3-0ubuntu3                                     amd64        HP SANE backend for multi-function peripherals
ii  sane-utils                                                  1.0.23-3ubuntu3                                     amd64        API library for scanners -- utilities
ii  xsane                                                       0.998-5ubuntu1                                      amd64        featureful graphical frontend for SANE (Scanner Access Now Easy)
ii  xsane-common                                                0.998-5ubuntu1                                      all          featureful graphical frontend for SANE (Scanner Access Now Easy)

```

Does that mean all of this stuff is installed? How come I *still* cannot scan with my scanner in third-party programs (as per my original question)?

---

### Post by pdc on 2014-04-18
> Does that mean all of this stuff is installed?  .............oh, yes............

[B]HOWEVER
[/B]
I notice you don't have [COLOR="#0000FF"]sane[/COLOR] installed eg **I have**

> ii  sane  1.0.14-9 scanner graphical frontends

eg from here [https://help.ubuntu.com/community/ScanningHowTo](https://help.ubuntu.com/community/ScanningHowTo)

(Sharing a Scanner over the Network)

> *All computers need to have Sane installed*: sudo apt-get install sane

so can I suggest you install sane > [COLOR="#FF0000"]sudo apt-get install sane[/COLOR]; 

can you check what works; and doesn't; after that

---

### Post by CybaCowboy on 2014-04-18
This is updated, after I installed SANE:

```

ii  libsane:amd64                                               1.0.23-3ubuntu3                                     amd64        API library for scanners
ii  libsane:i386                                                1.0.23-3ubuntu3                                     i386         API library for scanners
ii  libsane-common                                              1.0.23-3ubuntu3                                     amd64        API library for scanners -- documentation and support files
ii  libsane-hpaio                                               3.14.3-0ubuntu3                                     amd64        HP SANE backend for multi-function peripherals
ii  sane                                                        1.0.14-9                                            amd64        scanner graphical frontends
ii  sane-utils                                                  1.0.23-3ubuntu3                                     amd64        API library for scanners -- utilities
ii  xsane                                                       0.998-5ubuntu1                                      amd64        featureful graphical frontend for SANE (Scanner Access Now Easy)
ii  xsane-common                                                0.998-5ubuntu1                                      all          featureful graphical frontend for SANE (Scanner Access Now Easy)

```

Like before, I can scan with "Simple Scan"... But PDF Studio Pro (which requires me to share the scanner over the network via SANE) does not.

---

### Post by pdc on 2014-04-19
great; sane is now installed;

work your way through this guide

[https://help.ubuntu.com/community/ScanningHowTo#Sharing_a_Scanner_Over_a_Network](https://help.ubuntu.com/community/ScanningHowTo#Sharing_a_Scanner_Over_a_Network)

---

### Post by CybaCowboy on 2014-04-19
Yeah I already tried that (before you replied last) and I *still* have no luck... But I *did* find a work-around that works surprisingly well!

See, "Simple Scan" *only* scans documents in black and white, whilst photos are scanned in full color... If I scan a "photo" and then save it with the portable document format extension (".pdf"), SANE ignores the fact that it was actually scanned as an *photo* and automatically converts it to a *PDF file* (I know Ubuntu does this itself with the "print-to-file" feature if one manually changes the extension, so maybe it's *Ubuntu* doing this?)... Then all I've gotta do is open the file in PDF Studio Pro and *voilà*, instant scanning solution!

It's a *little* more work than I'm used to under Microsoft Windows and PDF Studio is *horrible* to look at, but I've been playing around with it all afternoon and it works *flawlessly*... It's also a _**lot**_ easier than the messy process to setup shared scanners (which in my experience, is difficult even by *Linux* standards!).

 Now all I need to find is a suitable DVD/Blu-Ray Disk "ripping" solution and I am good to go for a *single-boot* Ubuntu system (the scanning and Adobe Acrobat-quality alternative has been my biggest roadblocks, particularly with regards to the latter...)!

---

