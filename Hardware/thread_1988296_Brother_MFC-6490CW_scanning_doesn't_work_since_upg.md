---
title: "Brother MFC-6490CW scanning doesn't work since upgrade to Ubuntu 12.04"
date: 2012-05-27
forum: Hardware
---

### Post by Zvlwab on 2012-05-27
I have followed this guide for installing the scanner driver:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1b.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1b.html)
And this post:
[http://ubuntuforums.org/showthread.php?t=1439450](http://ubuntuforums.org/showthread.php?t=1439450)

This has always worked for me on Ubuntu 10.10.
But now on Xubuntu 12.04 it doesn't work anymore. Simple Scan says it couldn't find any printers.
Printing works fine though.

```
remco@laptop:~$ sudo dpkg -i --force-all ./brscan-skey-0.2.3-0.amd64.deb
Selecting previously unselected package brscan-skey.
(Reading database ... 224874 files and directories currently installed.)
Unpacking brscan-skey (from .../brscan-skey-0.2.3-0.amd64.deb) ...
Setting up brscan-skey (0.2.3-0) ...
remco@laptop:~$ sudo dpkg -i --force-all ./brscan3-0.2.11-4.amd64.deb 
Selecting previously unselected package brscan3.
(Reading database ... 224882 files and directories currently installed.)
Unpacking brscan3 (from ./brscan3-0.2.11-4.amd64.deb) ...
Setting up brscan3 (0.2.11-4) ...
remco@laptop:~$  dpkg -l | grep Brother
ii  brscan-skey                 0.2.3-0           Brother Linux scanner S-KEY tool
ii  brscan3                     0.2.11-4          Brother Scanner Driver
ii  mfc6490cwcupswrapper:i386   1.1.2-2           Brother CUPS Inkjet Printer Definitions
ii  mfc6490cwlpr:i386           1.1.2-2           Brother lpr Inkjet Printer Definitions
ii  printer-driver-ptouch       1.3-3             printer driver Brother P-touch label printers
remco@laptop:~$ brsaneconfig3 -a name=Scanner model=MFC-6490CW ip=192.168.2.109
remco@laptop:~$ brsaneconfig3 -q | grep Scanner
  0 Scanner             "MFC-6490CW"        I:192.168.2.109
remco@laptop:~$ dpkg -l | grep sane
ii  libsane                     1.0.22-7ubuntu1   API library for scanners
ii  libsane:i386                1.0.22-7ubuntu1   API library for scanners
ii  libsane-common              1.0.22-7ubuntu1   API library for scanners -- documentation and support files
ii  libsane-hpaio               3.12.2-1ubuntu3   HP SANE backend for multi-function peripherals
ii  sane-utils                  1.0.22-7ubuntu1   API library for scanners -- utilities
```

Also when I start my laptop it says saned is disabled. I don't know if that makes any difference. I did try starting saned, but Simple Scan still couldn't find any scanners.

---

### Post by kurt18947 on 2012-05-27
Is your system 32 bit or 64 bit?  I have the same device and am using it on 64 bit systems.  I did 3 things to get the scanner recognized by 64 bit 12.04 while it was in development.

1- This problem shows up in 12.04 as well as 11.10.  I think it might be a result of creating the driver as an .rpm package then converting to .deb using alien.  There was another manufacturer's .deb packages doing the same thing.
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00106](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00106)


2- This edit is needed for non-sudo users to be able to scan

Ubuntu 9.10, 10.04, 10.10, 11.4, 11.10, 12.041. 
Open "/lib/udev/rules.d/40-libsane.rules" file.  Add the following 2 lines.  The syntax will be obvious when you open the file.
# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"

Save the file and restart the OS.

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10)

3- I needed to add scanner users to the lp group.

I haven't installed the scanner since 12.04 was released so I don't know if #3 is still required.  I'm pretty sure #1 and #2 are, though.  Let us know how you get on.

---

### Post by Zvlwab on 2012-05-27
Yay it works! Thanks!
For other people having problems, this is what I did:

```
sudo cp /usr/lib64/libbrscandec3.so.1.0.0 /usr/lib
sudo cp /usr/lib64/sane/libsane-brother3.so.1.0.7 /usr/lib/sane
sudo cp /usr/lib64/sane/libsane-brother3.so.1 /usr/lib/sane
sudo cp /usr/lib64/sane/libsane-brother3.so /usr/lib/sane
sudo cp /usr/lib64/libbrscandec3.so /usr/lib
sudo cp /usr/lib64/libbrscandec3.so.1 /usr/lib
```

Edit: DON'T do the thing below, because apparantly it is not needed and it conflicts with the ia32-libs.
> Open "/lib/udev/rules.d/40-libsane.rules" file.  Add the following 2 lines.  The syntax will be obvious when you open the file.
# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"

---

### Post by ajgreeny on 2012-05-27
On a previous version of ubuntu I had to do the following to get a brother scanner on a similar multifunction machine to work.  It may be worth giving the same a try for 12,04

BROTHER SCANNER-
Install libsane-extras, then
    1. Open "/lib/udev/rules.d/40-libsane.rules" file.
    2.Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):
    The lines to be added:-

# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"

    3. Restart the OS.

---

### Post by kurt18947 on 2012-05-28
> **Zvlwab said:**
> Yay it works! Thanks!
For other people having problems, this is what I did:

```
sudo cp /usr/lib64/libbrscandec3.so.1.0.0 /usr/lib
sudo cp /usr/lib64/sane/libsane-brother3.so.1.0.7 /usr/lib/sane
sudo cp /usr/lib64/sane/libsane-brother3.so.1 /usr/lib/sane
sudo cp /usr/lib64/sane/libsane-brother3.so /usr/lib/sane
sudo cp /usr/lib64/libbrscandec3.so /usr/lib
sudo cp /usr/lib64/libbrscandec3.so.1 /usr/lib
```

:D :grin:

Could you mark this 'solved' (using thread tools at the top of the page) so other searchers might find it easily?  Enjoy.

---

### Post by BozeWolf on 2012-05-30
Instead of copying i linked the files, to prevent mismatching fileversions in the (possible) future

sudo ln -s /usr/lib64/libbrscandec3.so.1.0.0 /usr/lib
sudo ln -s /usr/lib64/sane/libsane-brother3.so.1.0.7 /usr/lib/sane
sudo ln -s /usr/lib64/sane/libsane-brother3.so.1 /usr/lib/sane
sudo ln -s /usr/lib64/sane/libsane-brother3.so /usr/lib/sane
sudo ln -s /usr/lib64/libbrscandec3.so /usr/lib
sudo ln -s /usr/lib64/libbrscandec3.so.1 /usr/lib


Edit: It works with dcp585-cw too.

---

### Post by enieffak on 2012-10-09
> **kurt18947 said:**
> 
2- This edit is needed for non-sudo users to be able to scan

Ubuntu 9.10, 10.04, 10.10, 11.4, 11.10, 12.041. 
Open "/lib/udev/rules.d/40-libsane.rules" file.  Add the following 2 lines.  The syntax will be obvious when you open the file.
# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"

Save the file and restart the OS.


Thank you! I upgraded from 11.04 gnome2 (amd64) to 12.10 mate-desktop-environment and my Brother MFC-6490CW didn't scan any longer with SimpleScan. With your help I got it working again.

(Upgrading didn't affect printing capability.)

---

### Post by sgori84 on 2012-11-12
Hi

i've got a Brother MFC-6490CW and Ubuntu 12.10.
The printer is connected with a WiFi router to my little office network.

I configured perfectly the "printer" but after almost 1000 tries i still can't scan directly from SimpleScan on Ubuntu (i've got the "no scanner" message from SimpleScan).
Is it possible that the wifi connection is not allowed for the scanning section of the printer? (i mean that maybe the network scanner work only with ethernet connection)

thank you in advance
sandro

---

### Post by sakal77 on 2013-02-20
Thank you! That is right for me and my printer/scanner MFC-240C :)

---

