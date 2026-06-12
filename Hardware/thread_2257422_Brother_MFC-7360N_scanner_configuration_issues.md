---
title: "Brother MFC-7360N scanner configuration issues"
date: 2014-12-19
forum: Hardware
---

### Post by dah2 on 2014-12-19
I hate to do this because there is quite a bit of information out there already.  Unfortunately, none of those tips are working.  I can't get the scanner on my Brother MFC-7360N to work.  What's more, I'm now at a point where  the superuser isn't even able to get it to work.  

_Using Simple Scan, the error is_
 Failed to scan
Unable to start scan

_Using xSane, the error is_
Failed to start scanner: Invalid argument

_The drivers are installed_
ddd@dale-OptiPlex-755:~/Downloads/BrotherScanner$ sudo dpkg -l|grep Brother
ii  brother-cups-wrapper-common                           1.0.0-10-0ubuntu6                                   amd64        Common files for Brother cups wrapper packages
ii  brother-udev-rule-type1                               1.0.0-1                                             all          Brother udev rule type 1
ii  brscan-skey                                           0.2.4-1                                             amd64        Brother Linux scanner S-KEY tool
ii  brscan4                                               0.4.2-1                                             amd64        Brother Scanner Driver
ii  cupswrappermfc7360n                                   2.0.4-2                                             i386         Brother MFC7360N CUPS wrapper driver
ii  mfc7360nlpr                                           2.1.0-1                                             i386         Brother MFC-7360N LPR driver
ii  printer-driver-ptouch                                 1.3-8                                               amd64        printer driver Brother P-touch label printers

_sane-find-scanner doesn't find a USB scanner._
  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.
[U]
scanimage does find a USB scanner[/U]
ddd@dale-OptiPlex-755:~/Downloads/BrotherScanner$ scanimage -L
device `brother4:bus2;dev1' is a Brother MFC-7360N USB scanner


I'm running Ubuntu 14.04

Who's ready to help me troubleshoot some more?

---

### Post by pdc on 2014-12-20
so did you edit the file > [COLOR="#008000"]/lib/udev/rules.d/40-libsane.rules[/COLOR] as Brother recommend?

[http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04](http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04)

one can do this either by downloading Brother's small deb package; that edits the file ..................or follow the Brother how-to that gives details

__________________________________________________________

>  What's more, I'm now at a point where the superuser isn't even able to get it to work.

.............can you tell us how you invoked the superuser please?

---

### Post by dah2 on 2014-12-20
I actually didn't have the file, so I downloaded the one Brother recommended. 

I use sudo for superuser.

---

### Post by pdc on 2014-12-20
so did you edit the file /lib/udev/rules.d/40-libsane.rules

---

### Post by dah2 on 2014-12-22
Yes, I've edited the file. It's no help.

---

### Post by pdc on 2014-12-22
in their FAQ

[http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00101](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00101)

Brother list a variety of files to copy from  /usr/lib64/ to /usr/lib/

for the brscan4 they say the files are /usr/lib64/sane/[COLOR="#008000"]libsane-brother4.so.1.0.7[/COLOR] and /usr/lib64/sane/[COLOR="#008000"]libsane-brother4.so[/COLOR] and /usr/lib64/sane/[COLOR="#008000"]libsane-brother4.so.1
[/COLOR]
____________

these are currently in [COLOR="#0000FF"]/usr/lib64/sane[/COLOR] so Brother would want them to go to [COLOR="#0000FF"]/usr/lib/sane[/COLOR]

so I think the commands are

```
cp /usr/lib64/sane/libsane-brother4.so.1.0.7 /usr/lib/sane 
```

```
cp /usr/lib64/sane/libsane-brother4.so /usr/lib/sane
```

```
cp /usr/lib64/sane/libsane-brother4.so.1 /usr/lib/sane
```

_______________________________

from here, [http://askubuntu.com/questions/327282/copying-multiple-specific-files-from-one-folder-to-another](http://askubuntu.com/questions/327282/copying-multiple-specific-files-from-one-folder-to-another)

I think one could do it in one go with ```
cp /usr/lib64/{libsane-brother4.so.1.0.7,libsane-brother4.so,sane/libsane-brother4.so.1} /usr/lib/sane
```

---

### Post by dah2 on 2014-12-28
There are already links from /usr/lib/sane to those files in /usr/lib64/sane.

---

### Post by dah2 on 2014-12-30
After looking a little closer, I discovered that lsusb reports the Brother device is on Bus 003 Device 002 while scanimage -L reports the Brother scanner on bus2;dev4. I'll keep digging, but if anyone has any quick thoughts as to why they're different, I'll take them. I'm assuming they should be reporting the same.

---

### Post by plucky on 2014-12-30
> **dah2 said:**
> After looking a little closer, I discovered that lsusb reports the Brother device is on Bus 003 Device 002 while scanimage -L reports the Brother scanner on bus2;dev4. I'll keep digging, but if anyone has any quick thoughts as to why they're different, I'll take them. I'm assuming they should be reporting the same.

Mine is the same ```
scanimage -L
device `brother2:bus1;dev4' is a Brother DCP-120C USB scanner
```

and ```
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 005: ID 046d:08ad Logitech, Inc. QuickCam Communicate STX
Bus 002 Device 004: ID 046d:c312 Logitech, Inc. DeLuxe 250 Keyboard
Bus 002 Device 003: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 002: ID 04f9:0190 Brother Industries, Ltd DCP-120C
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

My scanner works.

Have you installed sane-utils?

```
sudo apt-get install sane-utils
``` and then reboot.

Also post output for ```
dpkg -l | grep -i brother
```

Good Luck

---

### Post by dah2 on 2014-12-31
sane-utils is installed

dpkg -l | grep -i brother
```
ii  brother-cups-wrapper-ac                               1.0.3-1-0ubuntu3                                    amd64        Cups Wrapper drivers for ac brother printers
ii  brother-cups-wrapper-bh7                              1.0.0-10-0ubuntu6                                   amd64        Cups Wrapper drivers for bh7 brother printers
ii  brother-cups-wrapper-common                           1.0.0-10-0ubuntu6                                   amd64        Common files for Brother cups wrapper packages
ii  brother-cups-wrapper-extra                            1.2.1-0ubuntu4                                      amd64        Cups Wrapper drivers for extra brother printers
ii  brother-cups-wrapper-laser                            2.0.1-2-0ubuntu6                                    amd64        Cups Wrapper drivers for laser brother printers
ii  brother-cups-wrapper-laser1                           1.0.2-1-0ubuntu8                                    amd64        Cups Wrapper drivers for laser1 brother printers
ii  brother-cups-wrapper-mfc9420cn                        1.0.0-1-0ubuntu6                                    amd64        Cups Wrapper drivers for mfc9420cn brother printers
ii  brother-lpr-drivers-ac                                1.0.3-1-0ubuntu4                                    amd64        LPR drivers for ac brother printers
ii  brother-lpr-drivers-bh7                               1.0.1-1-0ubuntu6                                    amd64        LPR drivers for bh7 brother printers
ii  brother-lpr-drivers-common                            1.0.0-4-0ubuntu3                                    amd64        Common files for brother-lpr-drivers packages
ii  brother-lpr-drivers-extra                             1.2.0-2-0ubuntu5                                    amd64        LPR drivers for extra brother printers
ii  brother-lpr-drivers-laser                             2.0.1-3-0ubuntu5                                    amd64        LPR drivers for laser brother printers
ii  brother-lpr-drivers-laser1                            1.0.0-3-0ubuntu6                                    amd64        LPR drivers for laser1 brother printers
ii  brother-lpr-drivers-mfc9420cn                         1.0.0-3-0ubuntu4                                    amd64        LPR driver for mfc9420cn brother printer
ii  brother-udev-rule-type1                               1.0.0-1                                             all          Brother udev rule type 1
ii  brscan-skey                                           0.2.4-1                                             amd64        Brother Linux scanner S-KEY tool
ii  brscan4                                               0.4.2-1                                             amd64        Brother Scanner Driver
ii  cupswrappermfc7360n                                   2.0.4-2                                             i386         Brother MFC7360N CUPS wrapper driver
ii  mfc7360nlpr                                           2.1.0-1                                             i386         Brother MFC-7360N LPR driver
ii  printer-driver-ptouch                                 1.3-8                                               amd64        printer driver Brother P-touch label printers

```

---

### Post by plucky on 2014-12-31
Does ```
sudo simple-scan
``` see the scanner?

And post output for ```
lsusb
```

---

### Post by dah2 on 2015-01-01
applications open with sudo, but gets the errors identified in the original post.

lsusb results
```
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 003 Device 003: ID 0557:8021 ATEN International Co., Ltd 
Bus 003 Device 004: ID 0cf3:0036 Atheros Communications, Inc. 
Bus 003 Device 007: ID 04f9:0270 Brother Industries, Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by plucky on 2015-01-01
Not sure why your scanner doesn't work,but there is one command I would like you to try > Bus 003 Device 007: ID 04f9:0270 Brother Industries, Ltd 

```
sudo chmod a+w /dev/bus/usb/003/007
``` should change permissions for the scanner on that USB port.

Then see if simple-scan will see the scanner.

Good Luck

---

### Post by dah2 on 2015-01-01
Still no luck.  Again, neither app works with sudo, either.  Permissions don't currently seem to matter.

---

### Post by pdc on 2015-01-01
I did see some reports that 3.0usb ports had issues [http://askubuntu.com/questions/457901/usb-2-0-device-scanner-does-not-work-with-xhci-hcd-on-usb-3-0-system](http://askubuntu.com/questions/457901/usb-2-0-device-scanner-does-not-work-with-xhci-hcd-on-usb-3-0-system)

[https://wiki.archlinux.org/index.php/sane#Hangs_while_scanning_due_to_xhci_pre-boot_mode](https://wiki.archlinux.org/index.php/sane#Hangs_while_scanning_due_to_xhci_pre-boot_mode)

I am not sure if this could apply to you; I seem to remember what worked for these folks was to disable to xhci option in boot options

---

