---
title: "Scanner doesn't work anymore"
date: 2019-09-06
forum: Hardware
---

### Post by danielsender on 2019-09-06
I'm running Ubuntu 18.04.3 on two Dell Machines, a M6800 and a M6600. After a recent update the scanner, a Brother MFC-7820 stopped working with both machines. If I launch xsane I get the correct pop-up "Available devices" window, however when I click on the MFC-7820 I get another window saying

```
Failed to open device 'brother2:net1:dev0':
Invalid argument.
```

This problem is recent because the scanning was working fine until a couple of weeks ago.

I ran:

```
daniel@chopin:~$ scanimage -L
device `brother2:net1;dev0' is a Brother MFC-7820N MFC-7820N
device `brother2:bus2;dev1' is a Brother MFC-7820N USB scanner
device `brother4:net1;dev0' is a Brother MFC-L8900CDW MFC-L8900CDW
daniel@chopin:~$
```

the MFC-L8900CDW works fine.

I also ran: ```
daniel@chopin:~$ lsusb | grep Brother
Bus 003 Device 004: ID 04f9:0181 Brother Industries, Ltd MFC-7820N Port(FaxModem)
```

I will appreciate any help.

---

### Post by danielsender on 2019-09-07
Anybody there?

---

### Post by #&amp;thj^% on 2019-09-07
How Odd, just had a friend bring me his, but i had to edit:
```
/lib/udev/rules.d/40-libsane.rules
```
I just commented this: (Some where around line 40 I think)
```
# Brother scanners
#ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
```
Might be a conflict now, so first check and show us this please:
```
dpkg -l | grep Brother
```

---

### Post by #&amp;thj^% on 2019-09-07
Maybe see how this works:
```
scanimage --test -d 'brother2:net1;dev0'
```

---

### Post by danielsender on 2019-09-07
```
daniel@chopin:~$ scanimage --test -d 'brother2:net1;dev0'
Output format is not set, using pnm as a default.
scanimage: open of device brother2:net1;dev0 failed: Invalid argument
daniel@chopin:~$
```

and

```
daniel@chopin:~$ dpkg -l | grep -i brother
ii  brmfc7820nlpr:i386                            2.0.1-1                                      i386         Brother MFC-7820N LPR driver
ii  brother-udev-rule-type1                       1.0.2                                        all          Brother udev rule type 1
ii  brscan-skey                                   0.2.4-1                                      amd64        Brother Linux scanner S-KEY tool
ii  brscan2                                       0.2.5-1                                      amd64        Brother Scanner Driver
ii  brscan4                                       0.4.7-1                                      amd64        Brother Scanner Driver
ii  cupswrappermfc7820n:i386                      2.0.1-2                                      i386         Brother MFC7820N CUPS wrapper driver
ii  mfcl8900cdwcupswrapper:i386                   1.4.0-0                                      i386         Brother CUPS Laser Printer Driver
ii  mfcl8900cdwlpr:i386                           1.3.0-0                                      i386         Brother lpr Laser Printer Driver
ii  printer-driver-brlaser                        4-1                                          amd64        printer driver for (some) Brother laser printers
ii  printer-driver-ptouch                         1.4.2-3                                      amd64        printer driver Brother P-touch label printers
daniel@chopin:~$ 
```

---

### Post by danielsender on 2019-09-08
Any suggestions?

---

### Post by #&amp;thj^% on 2019-09-09
Will it show in:
```
scanimage -L
```
It might need something like:
```
brsaneconfig4 -a name=MyOwn665 model=MFC-665CW ip=192.168.1.234
```

---

### Post by danielsender on 2019-09-09
Sorry, I forgot to type 'name', here it goes again:

```
daniel@chopin:~$ scanimage -L
device `brother2:net1;dev0' is a Brother MFC-7820N MFC-7820N
device `brother2:bus2;dev2' is a Brother MFC-7820N USB scanner
device `brother4:net1;dev0' is a Brother MFC-L8900CDW MFC-L8900CDW
daniel@chopin:~$ brsaneconfig2 -a name=MFC-7820N model=MFC-7820N ip=192.168.2.17
"MFC-7820N" is already registered.
daniel@chopin:~$
```

---

### Post by #&amp;thj^% on 2019-09-09
What dose this show then:
```
cat /lib/udev/rules.d/40-libsane.rules
```

---

### Post by danielsender on 2019-09-09
In my system the file name is different:
```
daniel@chopin:~$ ls -last /lib/udev/rules.d/*sane*
4 -rw-r--r-- 1 root root 3543 Sep  1 02:31 /lib/udev/rules.d/60-libsane.rules
daniel@chopin:~$
```

looking at the timestamp, it seems very recent as if it was changed by an update. Here are its contents, that has no mention to any Brother scanner, however the MFC-8900CDW works fine.
```
daniel@chopin:~$ cat /lib/udev/rules.d/60-libsane.rules
# This file was automatically created based on description files (*.desc)
# by sane-desc 3.5 from sane-backends 1.0.28git
#
# udev rules file for supported USB and SCSI devices
#
# For the list of supported USB devices see /usr/lib/udev/hwdb.d/20-sane.hwdb
#
# The SCSI device support is very basic and includes only
# scanners that mark themselves as type "scanner" or
# SCSI-scanners from HP and other vendors that are entitled "processor"
# but are treated accordingly.
#
# If your SCSI scanner isn't listed below, you can add it to a new rules
# file under /etc/udev/rules.d/.
#
# If your scanner is supported by some external backend (brother, epkowa,
# hpaio, etc) please ask the author of the backend to provide proper
# device detection support for your OS
#
# If the scanner is supported by sane-backends, please mail the entry to
# the sane-devel mailing list (sane-devel@alioth-lists.debian.net).
#
ACTION!="add", GOTO="libsane_rules_end"


# The following rule will disable USB autosuspend for the device
ENV{DEVTYPE}=="usb_device", ENV{libsane_matched}=="yes", TEST=="power/control", ATTR{power/control}="on"


SUBSYSTEMS=="scsi", GOTO="libsane_scsi_rules_begin"
GOTO="libsane_rules_end"


LABEL="libsane_scsi_rules_begin"
KERNEL!="sg[0-9]*", GOTO="libsane_rules_end"


# Generic: SCSI device type 6 indicates a scanner
ATTRS{type}=="6", ENV{libsane_matched}="yes"


# Some scanners advertise themselves as SCSI device type 3


# Wildcard: for some Epson SCSI scanners
ATTRS{type}=="3", ATTRS{vendor}=="EPSON", ATTRS{model}=="SCANNER*", ENV{libsane_matched}="yes"


# Epson Expression 800 | Epson Expression 800
ATTRS{type}=="3", ATTRS{vendor}=="EPSON", ATTRS{model}=="Expression800", ENV{libsane_matched}="yes"


# Epson Perfection 2450 | Epson GT-9700F | Epson Perfection 2450 PHOTO
ATTRS{type}=="3", ATTRS{vendor}=="EPSON", ATTRS{model}=="GT-9700", ENV{libsane_matched}="yes"


# Epson Perfection 3200 | Epson GT-9800F | Epson Perfection 3200 PHOTO
ATTRS{type}=="3", ATTRS{vendor}=="EPSON", ATTRS{model}=="GT-9800", ENV{libsane_matched}="yes"


# Epson GT-X900 | Epson Perfection V700 Photo | Epson Perfection V750 Photo
ATTRS{type}=="3", ATTRS{vendor}=="EPSON", ATTRS{model}=="GT-X900", ENV{libsane_matched}="yes"


# Epson Perfection 636S | Epson Perfection 1200S | Epson Perfection 1200S
ATTRS{type}=="3", ATTRS{vendor}=="EPSON", ATTRS{model}=="Perfection1200", ENV{libsane_matched}="yes"


# Epson Perfection 636 | Epson Perfection 636S
ATTRS{type}=="3", ATTRS{vendor}=="EPSON", ATTRS{model}=="Perfection636", ENV{libsane_matched}="yes"


# Hewlett-Packard ScanJet 4p
ATTRS{type}=="3", ATTRS{vendor}=="HP", ATTRS{model}=="C1130A", ENV{libsane_matched}="yes"


# Hewlett-Packard ScanJet IIc
ATTRS{type}=="3", ATTRS{vendor}=="HP", ATTRS{model}=="C1750A", ENV{libsane_matched}="yes"


# Hewlett-Packard ScanJet IIp
ATTRS{type}=="3", ATTRS{vendor}=="HP", ATTRS{model}=="C1790A", ENV{libsane_matched}="yes"


# Hewlett-Packard ScanJet IIcx
ATTRS{type}=="3", ATTRS{vendor}=="HP", ATTRS{model}=="C2500A", ENV{libsane_matched}="yes"


# Hewlett-Packard ScanJet 4c
ATTRS{type}=="3", ATTRS{vendor}=="HP", ATTRS{model}=="C2520A", ENV{libsane_matched}="yes"


# Hewlett-Packard ScanJet 5p
ATTRS{type}=="3", ATTRS{vendor}=="HP", ATTRS{model}=="C5110A", ENV{libsane_matched}="yes"


# Hewlett-Packard ScanJet 6200C
ATTRS{type}=="3", ATTRS{vendor}=="HP", ATTRS{model}=="C6270A", ENV{libsane_matched}="yes"


# Hewlett-Packard ScanJet 6300C
ATTRS{type}=="3", ATTRS{vendor}=="HP", ATTRS{model}=="C7670A", ENV{libsane_matched}="yes"




LABEL="libsane_rules_end"
daniel@chopin:~$ 



```

---

### Post by #&amp;thj^% on 2019-09-09
Yup that is odd?
Try to add this to it then:
```
# Brother MFC-7820N
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="01e5", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"

```
I'm not sure if a reboot is required or not.
BTW Here is my list in the rules:
```
# Brother MFC-3100C
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="010e", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-5100C
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="010f", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-4800
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0110", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-6800 | Brother MFC 4600
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0111", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother DCP-1000
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0112", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-8500
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0113", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-9700
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0114", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-9800
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0115", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother DCP-1400
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0116", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother FAX-2900
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0117", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother FAX-3800
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0118", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-9660
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0119", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-9860
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="011a", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-9760
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="011c", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-9070
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="011d", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-9180
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="011e", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-9160
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="011f", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-580
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0120", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-590
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0121", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-5100J
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0122", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother FAX-2850
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0123", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-4800J
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0124", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-6800J
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0125", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother FAX1800C
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0126", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-9800J
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0127", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-8500J
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0128", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-9030
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="012b", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother FAX-4100
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="012e", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother FAX-4750e
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="012f", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother FAX-5750e
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0130", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-5200C
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0132", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-100
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0135", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-150CL
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0136", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-3200C
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="013a", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-890
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="013c", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-5200J
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="013d", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-4420C
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="013e", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-4820C
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="013f", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother DCP-8020
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0140", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother DCP-8025D
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0141", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-8420
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0142", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-8820D
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0143", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother DCP-4020C
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0144", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-3220C
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0146", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother FAX1820C
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0147", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-3320CN
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0148", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother FAX1920CN
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0149", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-3420C
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="014a", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-3820CN
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="014b", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother DCP-3020C
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="014c", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother FAX1815C
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="014d", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-8820J
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="014e", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother DCP-8025J
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="014f", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-8220
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0150", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-8210
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0151", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother DCP-1000J
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0153", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-3420J
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0157", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-3820J
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0158", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother DCP-8040
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="015d", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother DCP-8045D
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="015e", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-8440
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="015f", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-8840D
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0160", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-210C
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0161", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-420CN
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0162", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-410CN
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0163", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-620CN
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0165", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-610CLN
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0166", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-610CLN
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0168", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother DCP-110C
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0169", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother DCP-310CN
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="016b", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-5440CN
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="016d", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-5840CN
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="016e", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-3240C
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0173", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-3340CN
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0174", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-7420
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0180", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-7820N
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0181", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother DCP-7010
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0182", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother DCP-7020
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0183", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother DCP-7025
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0184", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-7220
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0185", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-7225N
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0186", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-9420CN
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="018a", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother DCP-115C
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="018c", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother DCP-116C
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="018d", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother DCP-117C
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="018e", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother DCP-120C
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0190", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother DCP-315CN
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0191", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother DCP-340CW
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0192", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-215C
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0193", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-425CN
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0194", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-820CW
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0195", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-640CW
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0197", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother DCP-8060
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="01a3", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-8460N
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="01a5", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-8860DN
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="01a6", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother DCP-330C
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="01a9", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-240C
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="01ab", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
# Brother MFC-7840W
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="01e5", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"

```

---

### Post by danielsender on 2019-09-10
I added those two lines, first with the idProduct 01e5 and with 0181 but it didn't make any difference. It is just giving me the same message. I'm stuck here.

---

### Post by danielsender on 2019-09-10
An interesting point of information is the speed of response. This scanner is configured both as a USB and a network scanner so when I call xsane the menu of scanners appears and if I select the USB option the response is immediate, while if I choose the networked one it takes a few seconds - ~10s - to bring the message, so it appears that the system goes actually to the network to call the scanner.

One more strange thing: if I cycle the power of the scanner, xsane will bring the scanning dialog once but it won't scan again with the same invalid message. Closing xsane and calling it again will go back to the "invalid" message directly without bringing the dialog.

---

### Post by him610 on 2019-09-10
Why do you have two versions of brscan?
```
ii  brscan2                                       0.2.5-1                                      amd64        Brother Scanner Driver
ii  brscan4                                       0.4.7-1                                      amd64        Brother Scanner Driver
```
I would think most recent version works with both mfc devices.

---

### Post by danielsender on 2019-09-10
I don't exactly remember, but I think that the Brother script to install the MFC-7820N calls that program. Should I try the brscan4 with that scanner?

---

### Post by him610 on 2019-09-10
> Should I try the brscan4 with that scanner?
No, I just checked which scanner driver version is listed at the Brother support page, [https://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfc7820n_all&os=128]("https://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfc7820n_all&os=128") and you actually have the correct version 0.2.5-1. Having two MFC devices configured on one computer might lead to issues in the configuration files. You have a brscan2 vers 0.2.5-1 and a brscan4 vers 0.4.7-1. 

I reread your original post and noticed this, 
```

device `brother2:net1;dev0' is a Brother MFC-7820N MFC-7820N
device `brother2:bus2;dev1' is a Brother MFC-7820N USB scanner

```
The network connection can be used(?) to initiate the scanner function on your MFC-7820N. That probably brings up another configuration issue. The fewer cables, the fewer chances of issues. 
(?) Well, maybe not. I just checked the release date for the MFC-7820N scanner driver; it was released in 2009 which makes it a little dated.  The MFC-7820N is the only machine that driver, brscan2 vers 0.2.5-1 is used on.
Sometimes upgrades break things. You might consider removing, followed by reinstalling the scanner driver for the MFC-7820N.
Is the other device, MFC-L8900CDW, used for scanning also?

---

### Post by danielsender on 2019-09-10
I already re-installed brscan2 but it didn't make any difference. Yes, the MFC-L8900CDW is also used for scanning but in a different room, sort of far away. This one works well. I repeat what I said in my original posting, both scanners were working well at the same time, it is only the MFC-7820N the one that is having issues now.

---

### Post by him610 on 2019-09-11
Noticed this today,
```

$ scanimage -L
device `brother2:net1;dev0' is a Brother MFC-7820N MFC-7820N
device `brother2:[COLOR="#FF0000"]bus2[/COLOR];dev1' is a Brother MFC-7820N USB scanner

```

```

$ lsusb | grep Brother
[COLOR="#FF0000"]Bus 003[/COLOR] Device 004: ID 04f9:0181 Brother Industries, Ltd MFC-7820N Port(FaxModem)

```
Don't know if the different bus assignments mean anything at all.
Shouldn't the MFC-7820N USB scanner show up when running *lsusb* ? I also realize that it may not show up at all. I have a Brother MFC-7360N and the only place mine shows up is when running *scanimage -L*; however I only have mine configured to print-scan-fax through the local network connections - none through USB ports. I have had issues in the past with wandering USB ports.

---

### Post by danielsender on 2019-09-11
Good point, I don't know if that difference is recent, that is after re-installation of brscan2 or that was like that before. Here is the sequence of the two commands again:

```
daniel@chopin:~$ scanimage -L
device `brother2:net1;dev0' is a Brother MFC-7820N MFC-7820N
device `brother2:bus2;dev1' is a Brother MFC-7820N USB scanner
device `brother4:net1;dev0' is a Brother MFC-L8900CDW MFC-L8900CDW
daniel@chopin:~$ lsusb | grep -i Brother
Bus 003 Device 008: ID 04f9:0181 Brother Industries, Ltd MFC-7820N Port(FaxModem)
daniel@chopin:~$ 
```

In any case, I think it shouldn't make any difference when attempting to use the local network device, right?

---

### Post by danielsender on 2019-09-11
This is bizarre to say the least! My machine has several USB ports, so I swapped the scanner connections and the scanner on the local network worked! The USB option still doesn't. Then I went back to the original USB port and the scanner on the network worked. It will continue working OK as long as I don't attempt to run the device connected to the USB port. I don't understand what does the USB connection have to do with the network configuration.

---

