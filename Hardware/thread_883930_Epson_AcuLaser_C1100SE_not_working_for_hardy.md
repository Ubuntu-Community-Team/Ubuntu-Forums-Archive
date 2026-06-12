---
title: "Epson AcuLaser C1100SE not working for hardy"
date: 2008-08-08
forum: Hardware
---

### Post by purewater08 on 2008-08-08
I think it should work using C1100's driver, I followed the method here:
[http://ubuntuforums.org/showthread.php?t=597629&highlight=c1100](http://ubuntuforums.org/showthread.php?t=597629&highlight=c1100)

My PC and the printer are connected through the gigabit switch. When I print something, the LED on switch blinks indicating data was sent thru the switch, but nothing reaches the printer.
Then I tried direct connection with usb cable, still the same.

Anyone got C1100SE working on hardy using the C1100 driver?

---

### Post by stchman on 2008-08-08
> **purewater08 said:**
> I think it should work using C1100's driver, I followed the method here:
[http://ubuntuforums.org/showthread.php?t=597629&highlight=c1100](http://ubuntuforums.org/showthread.php?t=597629&highlight=c1100)

My PC and the printer are connected through the gigabit switch. When I print something, the LED on switch blinks indicating data was sent thru the switch, but nothing reaches the printer.
Then I tried direct connection with usb cable, still the same.

Anyone got C1100SE working on hardy using the C1100 driver?

That printer is reported to work "Mostly" so it should do most things well.

[http://openprinting.org/show_printer.cgi?recnum=Epson-AcuLaser_C1100](http://openprinting.org/show_printer.cgi?recnum=Epson-AcuLaser_C1100)

When you installed the printer in Ubuntu I am assuming it found the IP address of the printer?

---

### Post by purewater08 on 2008-08-08
Yes, it found the IP address of the printer automatically.

And after following the steps in the last post here:
[https://answers.launchpad.net/ubuntu/+question/20375](https://answers.launchpad.net/ubuntu/+question/20375)
 
It works now!!  Thanks. :D 

One more thing, I checked "Toner Save Mode" and apply but the setting won't be saved. Here is the error_log:

E [09/Aug/2008:02:08:23 +0800] cupsdAuthorize: Local authentication certificate not found!
E [09/Aug/2008:02:08:23 +0800] cupsdAuthorize: Local authentication certificate not found!
E [09/Aug/2008:02:08:23 +0800] cupsdAuthorize: Local authentication certificate not found!
E [09/Aug/2008:02:08:23 +0800] cupsdAuthorize: Local authentication certificate not found!
E [09/Aug/2008:02:10:58 +0800] CUPS-Add-Modify-Printer: Unauthorized

Guess it's my cups config but not sure. :confused:

---

### Post by Marc Higgins on 2009-01-03
Firstly this might not work for everyone & there might be a better way (if you do know of one please share your knowledge & let me know).

It looks like something that ships with Ubuntu doesn't work with the Epson C1100 & the source file Epson-ALC1100-filter-1.2.tar.gz from epsons site [www.avasts.jp]("www.avasts.jp") doesn't work either (well I can't get it to work). However the rpm's available on the same site DO work if they are converted to deb's & installed.

#1 Install the dependencies (this is REALLY  important, if you don't do 
this it won't work)

```
sudo aptitude install gcc-3.3-base libstdc++5
```

or you could just use synaptic System > Administration > Synaptic & just search for & install gcc-3.3-base & libstdc++5

From here you can decide to;

[B]OPTION A
[B]
the simplest way to get your Epson C1100 printing on ubuntu is to just install the deb files direct from our site below[/B]
 
[http://www.hunny.be/epson-alc1100-filter_1.2-1_i386.deb]("http://www.hunny.be/epson-alc1100-filter_1.2-1_i386.deb")

[http://www.hunny.be/epson-alc1100-filter-cups_1.2-1_i386.deb]("http://www.hunny.be/epson-alc1100-filter-cups_1.2-1_i386.deb")


Just double click on EACH of these links, that will invoke the Gdebi package installer & install the files.

Then install the printer normally using System > Administration > Printers (AKA system-config-printer) & hopefully you will be printing happily in seconds :)

OR

OPTION B

you can make your own install files using Alien, the same way we did

Install Alien

```
sudo aptitude install alien

```
or just use synaptic System > Administration > Synaptic & search for & install alien

Then go to [URL="http://www.avasys.jp/english/linux_e/dl_laser.html"]http://www.avasys.jp/english/linux_e/dl_laser.html
[/URL]
download these 2 files

For Turbo/RedHat/Fedora (Epson-ALC1100-filter-1.2-0.i386.rpm)
For Turbo/RedHat/Fedora (Epson-ALC1100-filter-cups-1.2-0.i386.rpm)

then from a terminal run

```
sudo alien Epson-ALC1100-filter-1.2-0.i386.rpm

```

```
sudo alien Epson-ALC1100-filter-cups-1.2-0.i386.rpm

```
that will create 2 files

epson-alc1100-filter_1.2-1_i386.deb
epson-alc1100-filter-cups_1.2-1_i386.deb

you can then use dpkg -i

```
dpkg -i epson-alc1100-filter_1.2-1_i386.deb
```

```
dpkg -i epson-alc1100-filter-cups_1.2-1_i386.deb
```

or just double click the deb files with your mouse that will invoke the Gdebi package installer to install the files.

Then just install the printer normally using System > Administration > Printers (AKA system-config-printer) & hopefully you will be now be printing happily :)

---

