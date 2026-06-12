---
title: "Scanner on Epson nx515"
date: 2010-07-05
forum: Hardware
---

### Post by akxiii on 2010-07-05
Hello
I am trying to get my Epson Stylus nx515 all in one working. The printer was a cinch, and strangely works with either the nx400 or nx515 driver that it auto-found in the database.

The problem is that I can not get the scanner to work. Wired or wireless. I have tried it un/wired, with both drivers, and hitting the scan button vs going to Simple Scan. In any scenario the result is the same: The printer makes a noise like it is about to start and then locks up. It reads "scanning" on the display, but does nothing and the keys are unresponsive. I have to restart the printer to get it to respond.

In simple scan it finds the printer as "Epson PID 0856"

Any help would be appreciated.
I've tried using the _[Avaysis Linux Printer Driver ]("http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escpr/")_
I didn't find nearly as many options as in the forum links so the Avaysis site must have been updated (_[link to old forum post on the 515]("http://ubuntuforums.org/showthread.php?t=1365891&highlight=epson")_)
I made sure to change the driver to use the Avaysis one, and I didn't have any progress.

Has anyone had success in getting this up and running?
Could the printer itself be busted?

Thank you


Info about computers:
Lucid 10.04, 64bit
Karmic 9.10, 32bit

---

### Post by akxiii on 2010-07-05
I tried installing Avaysis on the 32bit Karmic box and when I went to reinstall the driver (plugged in via usb) I couldn't find a driver for the nx515. One step backwards I suppose.

I checked the lsusb and the epson.conf as someone suggested [on a different post]("http://ubuntuforums.org/showthread.php?t=1516586&highlight=epson+nx515&page=3") with no success.

---

### Post by ellgor on 2010-07-06
Hi,

Go to the "Avasys" site and get their Imagescan package, go through the form filling in bit( get the one nearest to yours) and when you get to the download page scroll right down until you see "Iscan or Imagescan deb" which is a completely seperate app  from the full printing package, once downloaded use gdebi to automatically install it, needs a reboot to work properly.

Regards, Ellgor.

---

### Post by akxiii on 2010-07-06
> **ellgor said:**
> Hi,

Go to the "Avasys" site and get their Imagescan package, go through the form filling in bit( get the one nearest to yours) and when you get to the download page scroll right down until you see "Iscan or Imagescan deb" which is a completely seperate app  from the full printing package, once downloaded use gdebi to automatically install it, needs a reboot to work properly.

Regards, Ellgor.

If you could visit the avasys site and let me know if this is what you are talking about I would appreciate it. I went there and I think they have redesigned the site since you have been there.
[http://avasys.jp/eng/](http://avasys.jp/eng/)
> Linux Drivers
> Downloads
> All in ones
> Epson Stylus NX515
scroll to bottom
> Dowload File: epson-inkjet-printer-escrp-1.0.0-1lsb3.2XXXXXX

This is what I tried, but I had seen others reference an "iscan" type package that I could not find on their site.

---

### Post by SoFl W on 2010-07-06
Although it is for another Epson try [this thread]("http://ubuntuforums.org/showthread.php?t=1393162"), mostly this [post]("http://ubuntuforums.org/showpost.php?p=9278753&postcount=6").  Your problem could be with adding your scanners IP address to the scanners config file.
I will check back later today.  I am busy now  but will try again later in the day.

---

### Post by SoFl W on 2010-07-06
Also you want to make sure you get the correct part of the download section at [http://avasys.jp/eng/](http://avasys.jp/eng/), see the attached picture.

---

### Post by akxiii on 2010-07-06
Woo yay! It works!

I had to download those two files, enter in the IP address and reboot.
Hip Hip Hooray!

I was about to give up.

---

### Post by akxiii on 2010-07-06
And it works through Simple Scan, so maybe the iscan software wasn't needed after all, just the network driver.

Just had to change the driver in preferences (in simple scan)

---

### Post by SoFl W on 2010-07-06
Cool!  Great to hear.

---

### Post by choochoousmc on 2010-11-28
I was following the thread fine until the end in working with the config file.
Ok name of the file and where is it located----please.
I did the avasys down loads.
The scanner worked one time then quit have same problem as everyone above.
I removed all the scan software from system.
Tried to reinstall the AVASYS downloads. Window came up saying other files needed to be removed also. But no option for removing them and don't know where they were located.
so just clicked install anyway.
But still back at beginning.
Never saw a option to provide IP address for the scanner, just the printer.
with simple scan it will start to scan then an error pops up saying lost communication with the scanner. 
Other scan software don't even see the scanner!

---

### Post by akxiii on 2010-11-28
> **choochoousmc said:**
> I was following the thread fine until the end in working with the config file.
Ok name of the file and where is it located----please.
I did the avasys down loads.
The scanner worked one time then quit have same problem as everyone above.
I removed all the scan software from system.
Tried to reinstall the AVASYS downloads. Window came up saying other files needed to be removed also. But no option for removing them and don't know where they were located.
so just clicked install anyway.
But still back at beginning.
Never saw a option to provide IP address for the scanner, just the printer.
with simple scan it will start to scan then an error pops up saying lost communication with the scanner. 
Other scan software don't even see the scanner!

Hello Friend,
Here is the definitive how to:
[LIST=1]
[*]Read this entire post.
[*]Download and install Avasys drivers
[LIST]
[*]iScan Driver
[LIST]
[*]For [64bit]("http://linux.avasys.jp/drivers/iscan/2.24.0/iscan_2.24.0-4.ltdl7_amd64.deb")
[*]For [32bit]("http://linux.avasys.jp/drivers/iscan/2.24.0/iscan_2.24.0-4.ltdl7_i386.deb")
[/LIST]
[*]Wireless Network Driver
[LIST]
[*]For [64bit]("http://linux.avasys.jp/drivers/scanner-plugins/iscan-network-nt/1.1.0/iscan-network-nt_1.1.0-2_amd64.deb")
[*]For [32bit]("http://linux.avasys.jp/drivers/scanner-plugins/iscan-network-nt/1.1.0/iscan-network-nt_1.1.0-2_i386.deb")
[/LIST]
[/LIST]
[*]Determine your printers IP address by going to *System > Administration > Printing*, then double click on your printer to view the location (ex. 10.0.0.3:515). If your printer is not there go to "Add" > Network Printer. Your printer should load in below the text Network Printer after a few seconds. Then follow the install guidelines selecting the Avasys driver.
[*]Enter your printers IP address in the driver configuration file */etc/sane.d/epkowa.conf*
```
gksudo gedit /etc/sane.d/epkowa.conf
```
Your ip address will be added in the format
```
net 10.0.0.3
```
[*]Log out and then back in
[*]After that you should be able to use simple scan to scan wirelessly.
[/LIST]

I am 90% certain that the driver/program iscan doesn't actually need to be installed, but that is how I did it and it worked. Best of luck.

---

### Post by c4mden on 2011-03-03
Thanks akxiii, those instructions worked perfectly for me.

---

