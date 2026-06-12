---
title: "No USB Scanner after Update"
date: 2011-08-24
forum: Hardware
---

### Post by floortester on 2011-08-24
[FONT=Comic Sans MS][SIZE=2]I am still a beginner even after 2 years of various Linux systems and have run into a problem that seems to have occurred a number of times according to the postings but not always with good outcomes. I am using version 11.04

I had been running "Simple Scan" using my Canon MP990 via USB with no problems but as Canon does not provide a Linux driver I could only print via TurboPrint. To improve the scanning ability I installed "Xsane" which gave much more facilities. I tried to install "Vuescan" but this was not recognised by the loader as an installation file.

I did a big Upgrade last week which took some 3-4 hours, I only do these when I have time to spare and after that Neither the  "Simple Scan" or "Xscan" could find the scanner with "No Scanners detected" or "No devices detected" error. I tried turning the scanner on after booting and also having it running before booting to no avail. I loaded the Sane Backend with the latest driver which included the Canon  printer but with no luck.

I ran the sane-find-scanner programme with no scanners detected on any port
I ran scanimage -L as root - no luck
I even tried Xsane as root despite the dire warnings but no luck.
I tried the Device Manager  which showed the MP 990 as an USB device on HUB Interface 1(of1) and a protocol of 09/00/00 with a USB interface of 1 (of 3) and a protocol of ff/00/ff
the PRINTING USB Interface was 2 (of 3) and a proto[/SIZE][/FONT][FONT=Comic Sans MS][SIZE=2]col of 07/01/02 its USB interface was 0 (of -1) and a protocol of ffffffff/ffffffff/ffffffff.

I have exhausted most options offered and all my manuals,

I would be very grateful for any advice given[/SIZE][/FONT][FONT=Comic Sans MS][SIZE=2]:confused:[/SIZE][/FONT]
[FONT=Comic Sans MS][SIZE=2]
Floortester[/SIZE][/FONT]

---

