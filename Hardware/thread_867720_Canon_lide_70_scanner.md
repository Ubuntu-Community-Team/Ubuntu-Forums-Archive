---
title: "Canon lide 70 scanner"
date: 2008-07-23
forum: Hardware
---

### Post by Ofloo on 2008-07-23
I have a scanner which is located by lsusb though is not working in xsane, .. the version of ubnutu, ubuntu-8.04.1-desktop-i386 is the iso I've installed on my laptop.

Also from Xsane i get an error something about /dev/video0 which is my webcam, .. and then it closes right away, ..

scanimage -L
device `v4l:/dev/video0' is a Noname HP Webcam virtual device

doesn't show my scanner in the device list so i'm guessing it's not detected.

---

### Post by phidia on 2008-07-23
Have you looked at the [supported devices section]("http://www.sane-project.org/cgi-bin/driver.pl?manu=canon&model=lide+70&bus=any&v=&p=") at the SANE site?
Searching for the LIDE 70 I see that it's listed as "unsupported".

---

### Post by Ofloo on 2008-07-23
Ok, .. do you know perhaps a tool which does support it ?

---

### Post by phidia on 2008-07-23
> **Ofloo said:**
> Ok, .. do you know perhaps a tool which does support it ?

Are you asking for a closed source solution? For printers there is turboprint which mostly is a pain IMO. I don't know of an equivilent to that for scanners though. Maybe someone else does. You could run windows in [virtualbox]("http://www.virtualbox.org/wiki/VirtualBox") that way you wouldn't have to reboot and it should let you use that scanner too.

---

### Post by trotsig on 2008-08-14
Confirm that it works in Hardy using VirtualBox (Sun xVM VirtualBox) while running WINXP. I enabled USB2 and presto it was found by WINXP, popped in the Canon install CD and it was working within minutes.... at least it's out of the closet now...

---

### Post by Ofloo on 2008-11-30
I have been looking around and i haven't found a real solution, so I was wondering if there is a scanner that is new and is supported by Linux, because scanners I am able to find are ancient and to me running windows is not a solution, why run linux at all if you're going to emulate windows 90% of the time, either run linux or don't, I don't get it most linux users bash windows but the first chance they get they either emulate it or dual boot it.

---

### Post by arepaking on 2009-06-09
Hello Everyone,

Did you figure it out how to use the scanner in Ubuntu? I have this very same model but I can't make it to work with Jaunty.

Thanks,
AK

---

### Post by kitrule on 2009-06-25
"The programming of the backend has been started. It will support scanners CanoScan LiDE 600F and CanoScan LiDE 70 as well. No code is published at the moment because everything is highly in flux."

[http://www.juergen-ernst.de/info_sane.html]("http://www.juergen-ernst.de/info_sane.html")

---

### Post by Berduchwal on 2012-08-13
This scanner comes up as lsusb:

Bus 001 Device 005: ID 04a9:2225 Canon, Inc. CanoScan LiDE 70

It does not work out of the box.

According to:
[https://answers.launchpad.net/ubuntu/+source/sane-backends/+question/115289](https://answers.launchpad.net/ubuntu/+source/sane-backends/+question/115289)

It simply does not work.

Website given above is for developers not end users so sadly this scanner is no go at this time. ([http://www.juergen-ernst.de/info_sane.html](http://www.juergen-ernst.de/info_sane.html))

---

