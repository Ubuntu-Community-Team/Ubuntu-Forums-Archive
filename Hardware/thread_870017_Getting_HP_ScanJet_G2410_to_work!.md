---
title: "Getting HP ScanJet G2410 to work!"
date: 2008-07-25
forum: Hardware
---

### Post by adityavpratap on 2008-07-25
Hi,
I have purchased this low-end flatbed scanner - HP Scanjet G2410. I can't get it to work in Ubuntu. sane-find-scanner detects it at libusb:001:003 and lsusb gives the following output -
Bus 001 Device 004: ID 03f0:0a01 Hewlett-Packard 
I have searched the web for a probable solution, but I found that it is not supported by sane. Is there any other way I can get it to work in Linux?
Thanking in advance,

---

### Post by phidia on 2008-07-25
At the scanner search from sane I didn't see that model although the hp G2710 is listed working "basic" Here's the [search list]("http://www.sane-project.org/cgi-bin/driver.pl?manu=hewlett+packard&model=scanjet+G2410&bus=any&v=&p=").

Try installing the hplip package(s) > sudo apt-get install hplip-gui

 And then open it from System>Preferences.

---

### Post by adityavpratap on 2008-07-25
With hplip-gui, I have to select manual search and then specify 001:003 on usb. Then the scanner is identified. When I click on next, I am presented with a list of ppd files to choose from, but no scanner drivers are listed here, only printer drivers.

---

### Post by phidia on 2008-07-25
> **adityavpratap said:**
> With hplip-gui, I have to select manual search and then specify 001:003 on usb. Then the scanner is identified. When I click on next, I am presented with a list of ppd files to choose from, but no scanner drivers are listed here, only printer drivers.

You may need to search for the driver file, but the hplip interface can be a little strange even in mac or windows. From [this page]("http://en.opensuse.org/SDB:Printer_Configuration_from_SUSE_LINUX_9.3_on") it seems like the ppd file could be for both a printer & a scanner but I don't know which one you need.

You could search the [HP Open Source page]("http://h71028.www7.hp.com/enterprise/cache/309906-0-0-0-121.html") for more info?

---

### Post by desertdog on 2010-03-04
You have two options.

1. There is a closed source driver for this scanner. For more information see: [http://lists.alioth.debian.org/pipermail/sane-devel/2009-January/023517.html](http://lists.alioth.debian.org/pipermail/sane-devel/2009-January/023517.html)

2. There is experimental/untested support for this scanner using the sane (open source). You would have to download the latest source code and compile from source. This tutorial tells you how to do this: [http://mp610.blogspot.com/2008/04/gi...shly-sane.html](http://mp610.blogspot.com/2008/04/gi...shly-sane.html)

---

### Post by adityavpratap on 2010-03-04
Hi,
Thanks for your reply! I'll try out your suggestions.

---

### Post by soulitude on 2010-08-29
adityavpratap,

Hi Aditya .. did you manage to install and get it running? Please post the results and the steps you followed. Did you try those solutions from desertdog?
Thank you.

---

### Post by adityavpratap on 2010-08-29
Hi,
I simply followed the steps delineated here (follow these links) -
[http://http://old.nabble.com/HP2400-HP2400c-HP-G2410-Re-Indian-Driver-td21374472.html#a21374472]("http://http://old.nabble.com/HP2400-HP2400c-HP-G2410-Re-Indian-Driver-td21374472.html#a21374472")
and
[http://erratwork.wordpress.com/2009/10/30/scanner-hp-g2410-on-ubuntu-yes-its-possible/]("http://erratwork.wordpress.com/2009/10/30/scanner-hp-g2410-on-ubuntu-yes-its-possible/")
and now my scanner works!!
Basically the second link gives the same method, except where it gives a solution for the following error -
> Failed to open device ' hp2400:libusb:003:002': Access to resource has been denied

---

### Post by soulitude on 2010-08-29
Thanks a lot Aditya ... you are a pal :) and glad it worked for you!

---

### Post by adityavpratap on 2010-08-29
Glad it work for you too! :-)

---

### Post by soulitude on 2010-08-29
Hi Aditya,

Actually it is for my friend, he is new to linux and this was his need, so i thought i'll follow up a little. Any way thanks a lot.

I hope your scanner works well for both color as well as black and white scans ... have you faced any problems with scanning black and white images? he said he had tough times with that, while color works fine.

---

### Post by adityavpratap on 2010-08-30
b/w and color scanning are working fine!

---

### Post by gywst on 2011-03-05
I have a hp scanjet 2400 (HP ScanJet G2410). I installed [HPLIP Toolbox]("hplipopensource.com") (HP Linux Imaging and Printing Print, Scan and Fax Drivers for Linux) and I was able to scan with [Simple Scan 2.32.0]("https://launchpad.net/simple-scan"):

```
sudo apt-get install hplip-gui
```

---

### Post by yugo4k on 2011-05-05
Unfortunately, this didn't work for me... I tried all variants of the procedure I found in the web to no good. It went as far as **sane-find-scanner** actually finding scanjet, but **scanimage -L** kept outputting that it did not recognize any scanners.

Then I tried the lite session of 11.04 and the scanner was already working there. I guess I'll just stop using 10.04... seems simpler... :)

---

### Post by yugo4k on 2011-05-05
Oh dang. I hate when that happens.

I was just closing the browser tabs on g2410 and 10.04 (using lucid) when I noticed I did not change the permission on **/dev/bus/usb/###/$$$** recognized by **sane-find-scanner**. I gave it a try... and **scanimage -L** actually recognized my scanner!

I was all happiness until the scanned page on **Simple Scan** was garbage. I tried **XSane Image Scanner** just to get the message:
"Error - Failed to start scanner: invalid argument - Close"

And the 11.04 installation is crashing for unknown reasons. Oh well.

---

### Post by desertdog on 2011-06-14
Support for the G2410 and 2400c was recently updated.

Try compiling the latest source code.

[https://help.ubuntu.com/community/CompileSaneFromSource](https://help.ubuntu.com/community/CompileSaneFromSource)

---

### Post by adityavpratap on 2011-06-14
Well, that's great news!

---

### Post by Ilovecomputers on 2011-11-13
> **phidia said:**
> At the scanner search from sane I didn't see that model although the hp G2710 is listed working "basic" Here's the [search list]("http://www.sane-project.org/cgi-bin/driver.pl?manu=hewlett+packard&model=scanjet+G2410&bus=any&v=&p=").

Try installing the hplip package(s)  And then open it from System>Preferences.

I tried this and it didnt work. it created a driver for hp printers. i have a hp scanjet 3970. i cannot find a driver for this and have no clue as to how to get it to work. without my scanner i wont be able to use ubuntu. can any one help? is it possible to get the scanner to work with ubuntu or not?

---

