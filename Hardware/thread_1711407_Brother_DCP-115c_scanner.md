---
title: "Brother DCP-115c scanner"
date: 2011-03-21
forum: Hardware
---

### Post by turiontzukosson on 2011-03-21
Hi there!

Some while ago (very probably over half a year = release period of Ubuntu) I made my Brother DCP-115c scanner work. I don't remember exactly how I did it.

Anyway, I reinstalled my system some time ago and now it doesn't work anymore. I have an up-to-date Kubuntu 10.10 on an HP Compaq nx6325. The following commands give the outputs:

```
$ lsusb
Bus 003 Device 005: ID 04f9:018c Brother Industries, Ltd DCP-115C

$ dpkg -l | grep Brother
ii  brother-cups-wrapper-common                                      1.0.0-10-0ubuntu5                                 Common files for Brother cups wrapper packages
ii  brscan-skey                                                      0.2.1-3                                           Brother Linux scanner S-KEY tool
ii  brscan2                                                          0.2.5-1                                           Brother Scanner Driver

$ sane-find-scanner
#Blabla
found USB scanner (vendor=0x04f9, product=0x018c) at libusb:003:005
#Blabla

$ sudo scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
```
Note, that I called scanimage with root privileges, so this is not some privilege confusion, but some real problem.

I tried everything relevant I found on the first three google pages to that problem, including the instructions on [http://wiki.ubuntuusers.de/Brother/Scanner](http://wiki.ubuntuusers.de/Brother/Scanner) and I don't have any idea what to now. Can you help me?

---

### Post by Pulka on 2011-03-21
having the same problem.
My scanner was working perfectly for a year now, but after some updates (don't know for sure if this was the problem) it doesn't recognize the scanner anymore. 
The printer works fine, and scanner works in other computers and OS.

I have ubuntu 10.10 installed

---

### Post by Pulka on 2011-03-21
ok...weird stuff

a few days ago tried to install all the drivers again and didn't work.
Today, tried again and it works.

Try to do all the steps from the brother support page. Worked for me

---

