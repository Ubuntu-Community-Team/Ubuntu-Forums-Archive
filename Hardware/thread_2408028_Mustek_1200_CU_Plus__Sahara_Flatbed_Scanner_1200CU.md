---
title: "Mustek 1200 CU Plus / Sahara Flatbed Scanner 1200CU Plus"
date: 2018-12-12
forum: Hardware
---

### Post by jarvis.izbach on 2018-12-12
I am currently running LUBUNTU 18.04 on my Dell Latitude D620.

Installed XSane and it worked perfectly with my CANOSCAN 9000F.

I had the Sahara Flatbed Scanner 1200CU Plus lying around and since it is more portable 
I decided to try it out.

It failed connectivity and XSane could not open and register it, so I did some looking around.
The simple fix is:
Downloaded driver file from [http://www.meier-geinitz.de/sane/gt68xx-backend/](http://www.meier-geinitz.de/sane/gt68xx-backend/)
[TABLE]
[TR="class: g, bgcolor: #90FF90"]
[TD]Mustek[/TD]
[TD]BearPaw 1200 CU Plus[/TD]
[TD]CIS[/TD]
[TD]6816[/TD]
[TD]0x055f[/TD]
[TD]0x021b[/TD]
[TD][PS1Gfw.usb]("http://www.meier-geinitz.de/sane/gt68xx-backend/firmware/PS1Gfw.usb")

[/TD]
[/TR]
[/TABLE]

  su -
  mkdir /usr/share/sane/gt68xx/
  cp PS1fw.usb /usr/share/sane/gt68xx/
  chmod a+r /usr/share/sane/gt68xx/PS1fw.usb
Voila .... Xsane opened and works fine with the scanner.

Hope this helps someone

---

### Post by barnesd1 on 2019-06-24
My Packard Bell 1200 CU Plus scanner is recognised by Ubuntu with lsusb as
Bus 002 Device 010: ID 055f:021b Mustek Systems, Inc. BearPaw 1200 CU Plus
I installed simple-scan with sudo apt install simple-scan - the scanner couldn't be found
I had the BearPaw zip file I used to install on Windows called 1_MustekBearPaw12.zip
I extracted the two .usb files from zip and put them in the new folder you suggested /usr/share/sane/gt68xx
Then from terminal I ran simple-scan
It says that /usr/share/sane/gt68xx/SBSfw.usb could not be found
First I copied one usb file sudo cp PS1Gfw.usb SBSfw.usb and tried to scan, that didnt work
Then I unplugged and replugged in the scanner and copied the other one with sudo cp PS1Dfw.usb SBSfw.usb
This worked, and on 19.04 too!
regards
David

---

