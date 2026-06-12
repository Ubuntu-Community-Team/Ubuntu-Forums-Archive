---
title: "Installing Brother DCP7055W Scanner - tried everything!"
date: 2016-03-31
forum: Hardware
---

### Post by csak9292 on 2016-03-31
Hello Ubuntu Experts!

It seems that I have a quite common problem, i can't get my DCP7055w scanner working. I tried everything posted on this forum and in the ubuntu wiki.  Maybe you can help. Here some informations:

lsusb gives me the follwing:

Bus 002 Device 004: ID 0a5c:21ec Broadcom Corp. 
Bus 002 Device 003: ID 046a:010d Cherry GmbH 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 04f9:02ce Brother Industries, Ltd 
Bus 001 Device 004: ID 046d:c069 Logitech, Inc. M-U0007 [Corded Mouse M500]
Bus 001 Device 003: ID 174c:5106 ASMedia Technology Inc. ASM1051 SATA 3Gb/s bridge
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

scanimage -L

device `bus2;dev1' is a Brother DCP-7055W USB scanner

scanimage -d "bus2:dev1" --format tiff > rawr.tiff
scanimage: open of device bus2:dev1 failed: Invalid argument

scanimage -d "bus1:dev5" --format tiff > rawr.tiff
scanimage: open of device bus1:dev5 failed: Invalid argument

dpkg -l | grep Brother

ii  brother-udev-rule-type1                       1.0.0-1                                    all          Brother udev rule type 1
rc  brscan                                        0.2.4                                      amd64        Brother CUPS Printer Definitions
ii  brscan-skey                                   0.2.4-1                                    amd64        Brother Linux scanner S-KEY tool
ii  brscan4                                       0.4.3-3                                    amd64        Brother Scanner Driver
ii  dcp7055wcupswrapper:i386                      3.0.1-1                                    i386         Brother DCP-7055W CUPS wrapper driver
ii  dcp7055wlpr:i386                              3.0.1-1                                    i386         Brother DCP-7055W LPR driver




Same problem for xsane and simple-scan, both give me the invalid argument message.
I also editet the libsane rules file , scanner is on a USB 2 Port and not on a hub.  
I'm running Ubuntu 15.10.


I am totally out of ideas now, please help an ubuntu newbie! :)

---

### Post by him610 on 2016-03-31
Is this you machine...
[HTML]http://www.brother.co.uk/printers/mono-laser-printers/dcp7055w[/HTML]

This is actually an internal USB hub within your computer.
```
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

This is a Brother machine; unless you have another Brother device connected, this _*is your Brother DCP7055w*_
```
Bus 001 Device 005: ID 04f9:02ce Brother Industries, Ltd
```


Did you download Brother drivers from this page...
[HTML]http://support.brother.com/g/b/downloadlist.aspx?c=gb&lang=en&prod=dcp7055w_us_eu_as&os=128[/HTML]

The Driver Install Tool (DIT), listed on the page, actually works very well. Properly installed, it will install your printer and scanner drivers.

If you download the DIT and follow the instructions, you should not have any problems; however, you need to get your system back to the pristine condition it was in before you started screwing it up.

---

### Post by csak9292 on 2016-04-01
Removed all drivers and installed them like you said, nothing helped. (did it multiple times before) Like i said, i am out of ideas .... :(

---

### Post by plucky on 2016-04-01
Have you installed sane-utils?

```
sudo apt-get install sane-utils
```

Then reboot and see if you can see the scanner.

Please post output for ```
dpkg -l | grep -i brother
``` again.

Good Luck

---

### Post by csak9292 on 2016-04-01
Hi,

dpkg -l | grep -i brother
ii  brscan-skey                                   0.2.4-1                                    amd64        Brother Linux scanner S-KEY tool
ii  brscan4                                       0.4.3-3                                    amd64        Brother Scanner Driver
ii  dcp7055wcupswrapper:i386                      3.0.1-1                                    i386         Brother DCP-7055W CUPS wrapper driver
ii  dcp7055wlpr:i386                              3.0.1-1                                    i386         Brother DCP-7055W LPR driver


Of course I got sane-utils,   tried to scan with several tools (simple-scan, gscan2pdf, skanlite, xsane, scanimage itself)
Tried to scan as root also....must be something else.    

I don't want to but do you suggest downgrading from ubuntu 15.10 to an older kernel
Some more information if you need:

dpkg -l | grep scanner

ii  brscan-skey                                   0.2.4-1                                    amd64        Brother Linux scanner S-KEY tool
ii  libksane-data                                 4:15.08.2-0ubuntu1                         all          scanner library (data files)
ii  libksane0                                     4:15.08.2-0ubuntu1                         amd64        scanner library (runtime)
ii  libsane:amd64                                 1.0.25+git20150528-1ubuntu2                amd64        API library for scanners
ii  libsane-common                                1.0.25+git20150528-1ubuntu2                all          API library for scanners -- documentation and support files
ii  libzbar0                                      0.10+doc-10build1                          amd64        bar code scanner and decoder (library)
ii  sane                                          1.0.14-11                                  amd64        scanner graphical frontends
ii  sane-utils                                    1.0.25+git20150528-1ubuntu2                amd64        API library for scanners -- utilities
ii  skanlite                                      1.1-0ubuntu1                               amd64        image scanner for KDE 4 based on the KSane backend

---

### Post by csak9292 on 2016-04-01
Is there any other useful information i could provide?

---

### Post by plucky on 2016-04-01
> dpkg -l | grep -i brother
ii brscan-skey 0.2.4-1 amd64 Brother Linux scanner S-KEY tool
ii brscan4 0.4.3-3 amd64 Brother Scanner Driver
ii dcp7055wcupswrapper:i386 3.0.1-1 i386 Brother DCP-7055W CUPS wrapper driver
ii dcp7055wlpr:i386 3.0.1-1 i386 Brother DCP-7055W LPR driver


What is missing is from the list ```
ii  brother-udev-rule-type1                               1.0.0-1                                             all          Brother udev rule type 1
```

Go [Here](http://support.brother.com/g/b/downloadlist.aspx?c=gb&lang=en&prod=dcp7055w_us_eu_as&os=128) and download and install the Scanner Setting File (deb) package and install using the Software Centre.

You will need to reboot after the install.

Good Luck

If that doesn't work,you should run these two commands ```
sudo cp /usr/lib64/* /usr/lib
sudo cp /usr/lib64/sane/* /usr/lib/sane
``` as you installed the amd64 version of the scanner driver.

These commends copy the scanner files in usr/lib64/ to /usr/lib and /usr/lib64/sane into /usr/lib/sane.

A reboot might again be needed.

---

### Post by csak9292 on 2016-04-01
I had it installed and tried the workaround from post#2, forgot the rules file.  I installed it and copied the files but it wont work either. (Did this before also :( )

Also tried different usb ports AND network implementation, neither of this options worked.  I am relatively new to linux and i really want to use it but things like that are a pain in the ass. Its not a scanner problem, scanning works perfect with windows, printing works for both OS.

I also tried different possibilities in editing the .rules file (different groups, different modes 0666 and 0664, ...etc.). There must be a different solution.   I found a command line in another forum that tells me about a blockage of the usb port, i tried the following command but it wasn't the solution either:  

before scanning : sudo modprobe -r usblp usb_storage   
modprobe: FATAL: Module usb_storage is in use.

afterwards:        sudo modprobe usblp usb_storage

aahhhh. i want to throw my scanner out of the f* ing window.

BTW if i try scanimage >imagename.tiff
scanimage: rounded value of br-x from 215.9 to 215.88
scanimage: rounded value of br-y from 355.6 to 355.567
scanimage: sane_start: Invalid argument

---

### Post by csak9292 on 2016-04-01
[B][U]I MADE IT, IT FINALLY WORKS!!!
[/U][/B]
Installed it as a network printer/scanner.    still not usable via USB. (still this issue is interesting....)

Thanks for the time! :)

---

