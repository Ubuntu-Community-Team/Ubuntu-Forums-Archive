---
title: "Samsung Galaxy S5 drivers for Ubuntu"
date: 2015-03-23
forum: Hardware
---

### Post by jerry43 on 2015-03-23
I currently use a Samsung Galaxy S3 with Ubuntu. I switch between Ubuntu 12.04 and Ubuntu 14.04. In order for me to mound the internal storage of my phone I must use mtp-tools and/or gmtp. Sometimes, my SD card will mount, but sometimes I must physically remove my SD card, and put it into an SD card adapter for it to be able to be read. In addition, I must have my phone in camera transfer mode as opposed to a proper USB transfer mode if I want to transfer files. My Samsung Galaxy S3 sometimes gets properly mounted in Windows 7. My Samsung Galaxy S3 is a grey imported phone, and although the hardware is correct, sometimes there are software glitches. I am asking this, because I am planning to buy a new Samsung Galaxy S5 soon. I would like to know if there is better support of Samsung Galaxy S5 in Ubuntu than the Samsung Galaxy S3. Does Ubuntu 14.04 have native support for Samsung Galaxy S5? Or is there additional software I must install in addtion to mtp-tools and/or gmtp? I do plan to buy a totally real Samsung Galaxy S5 as opposed to a grey imported one. Ideally, I don't want to have to take my SD card out of my phone every time I want to get the data off of the SD card. I would like it to be as convenient as Windows 7 makes it. I would appreciate help on this matter. All help on this matter is appreciated. ):P

---

### Post by westie457 on 2015-03-24
Welcome jerry43
This might be of some help to you.  [http://ubuntuforums.org/showthread.php?t=2226702](http://ubuntuforums.org/showthread.php?t=2226702)

---

### Post by Mark Phelps on 2015-03-24
For Windows 7, you should download and install Samsung Kies 3.  That will automatically download and install the latest Samsung drivers for your phone.  It also has lots of cool features, like the ability to backup the contents of the phone.

---

### Post by efflandt on 2015-03-25
I have an S3 and never could get MTP working properly in 12.04 even trying various other things (probably mtptools and/or gmtp), so at that time I resorted to using Android apps **ConnectBot** (ssh client), **AndFTP** (sftp client), and **SSHServer** (to ssh, scp, or sftp in other direction) using my Linux openssh keys via WiFi.

But I have had no problems accessing files on my S3 or its microSD via USB cable in 13.10 or 14.04. The only issue is that from Linux I cannot open files (images, videos, etc.) "on" the phone, I have to download them to Linux first before I can open them.

In any of them (even 12.04) USB tethering to mobile data worked automatically without doing anything, which came in handy when my DSL was acting up. I simply connected USB cable, enabled tethering on S3, and Ubuntu connected through USB as though it was Ethernet and disconnected my WiFi. Note that using the phone for tethering or as WiFi hotspot requires a suitable data plan that allows that.

---

