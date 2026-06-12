---
title: "Scanner not detected. Brother DCP-7030 / 12.04"
date: 2012-04-28
forum: Hardware
---

### Post by Chris_no on 2012-04-28
Installed 12.04 yesterday I perviously had 10.04 with no issues.

Everthing went right up except my scanner.
xsane is installed and also simple scan.
Neither sees the scanner.
The printer works just fine.

I have followed this guide to no avail... (Worked in 10.04)

```
http://ubuntuforums.org/showthread.php?t=1340908
```

These are the scanner drivers I used:
```

http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/brscan3-0.2.11-4.amd64.deb&lang=English_gpl
```

```
http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/brscan-skey-0.2.3-0.amd64.deb&lang=English_lpr
```

**I'v added my user to both saned and scanner group.**

I tried installing them with and without ```
**dpkg --force-all**
```

```
**lsusb**
```
outputs
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 001 Device 004: ID 041e:4083 Creative Technology, Ltd Live! Cam Socialize [VF0640]
**Bus 002 Device 002: ID 04f9:01ea Brother Industries, Ltd DCP-7030**
```

```

**sudo dpkg -l | grep Brother**
```
outputs
```
ii  brdcp7030lpr:i386                      2.0.2-1                                 Brother DCP-7030 LPR driver
rH  brscan                                 0.2.4                                   Brother CUPS Printer Definitions
ii  brscan-skey                            0.2.3-0                                 Brother Linux scanner S-KEY tool
ii  brscan3                                0.2.11-4                                Brother Scanner Driver
ii  cupswrapperdcp7030:i386                2.0.2-1                                 Brother DCP7030 CUPS wrapper driver
ii  printer-driver-ptouch                  1.3-3                                   printer driver Brother P-touch label printers
```

```
**brscan-skey -l**
```
outputs
```
DCP-7030          : brother3:bus1;dev1  : USB                  Not Registered
```

With
```
**sudo gedit /lib/udev/rules.d/40-libsane.rules**
```

I've added
```
# Brother scanners
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="01ea", ENV{libsane_matched}="yes"
```

to the end and restarted.

I tried putting it over the end rules label and end usb rules label
and restarting with no effect either way.

With
```
**sudo gedit /lib/udev/rules.d/50-udev-default.rules**
```

I've changed
```
# 'libusb' device nodes
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0665"
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", IMPORT{builtin}="usb_id"
```
to
```
# 'libusb' device nodes
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", IMPORT{builtin}="usb_id"
```

I'm all out of ideas so I will post this here while i search for
other solutions.

Solution:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101)

I copied these
```

cp /usr/lib64/libbrscandec3.so.1.0.0 /usr/lib
cp /usr/lib64/sane/libsane-brother3.so.1.0.7 /usr/lib/sane
cp /usr/lib64/sane/libsane-brother3.so.1 /usr/lib/sane
cp /usr/lib64/sane/libsane-brother3.so /usr/lib/sane
cp /usr/lib64/libbrscandec3.so /usr/lib
cp /usr/lib64/libbrscandec3.so.1 /usr/lib

```

---

### Post by virenjj on 2012-04-29
I have same issue brother printer DCP-7040 printer works but not scanner. Followed instruction posted above but getting following error:


$ cp /usr/lib64/libbrscandec2.so.1.0.0 /usr/lib
cp: `/usr/lib64/libbrscandec2.so.1.0.0' and `/usr/lib/libbrscandec2.so.1.0.0' are the same file


Not able to scan using DCP-7040. It used to work in 10.10 but since I upgraded to 11.10, it does not work

---

### Post by gecka on 2012-05-07
See the Brother FAQ, works in 12.04:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101)

---

### Post by Erszebet Lunah on 2012-05-08
Hi, I too have this problem where printing works but scanner isn't detected.
I tried everything described in this post but nothing seems to work :-/

I switched to sane backend version 1.0.19 which used to work on my previous Ubuntu install (10.11)
 but ever since the upgrade to 11.04 (and now 12.04) I never got scanning to work with my DCP-7040...

---

### Post by CactusCoderCA on 2012-06-06
> **gecka said:**
> See the Brother FAQ, works in 12.04:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101)

**/usr/lib64** does not exist in my 12.04 64-bit install.

When I print I do get the status message that the job is printing and then that the job has finished printing, but nothing is ever sent to the printer.

The scanner is not recognized at all.

Got the printer to work by using CUPS ([http://localhost:631/](http://localhost:631/)) and selecting the **Brother DCP-7020 Foomatic/hl1250 (recommended)** driver.

No scanning yet...

---

### Post by calmher on 2013-01-19
I wasn't going anywhere as well with the solution above. Here is what I did with my 64-bit system:

[LIST=1]
[*]Make sure DCP-7030 is turned on and usb is plugged in to your machine. 

[*]Removed brscan3 2.11-4:
```
dpkg -r brscan3-0.2.11-4.i386.deb
```

[*]Check that brscan3 isn't there anymore by:
```
dpkg -l | grep Brother
```

[*]Reboot.

[*]Download brscan3 2.11-5 (brscan3 64bit) from [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html#brscan3](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html#brscan3)

[*]Install it by:
```
dpkg -i --force-all brscan3-0.2.11-5.amd64.deb
```
[/LIST]

Works perfectly for me :D

---

### Post by Tshann on 2013-04-29
If none of the above work, what worked for me was to go to the brother site. The issue is that - at least with Brscan2 x64 - that the drivers are installed to the wrong directory. go to [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html") if you look @ the section: that says 

> I'm using Ubuntu 11.10 or higher. I cannot scan from my Brother Machine.

the instructions say to copy some files - that was what ultimately solved it for me. I expected that when I installed the Brother linux drivers, that was it. But no, the drivers installed to directories that my version of ubuntu (linux mint Nadia Xfce x64) doesn't use. So copying those files over immediately solved it.

---

### Post by krzysztofwitek on 2013-05-19
It worked for me after changing permissions on usb devices:
sudo chmod o+wr /dev/bus/usb/00*/*

---

