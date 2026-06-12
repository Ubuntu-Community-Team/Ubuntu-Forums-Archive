---
title: "problem in using iscan by Epson CX9300F"
date: 2010-03-17
forum: Hardware
---

### Post by fered on 2010-03-17
[COLOR=Blue][B]Hi
After downloading and installing iscan and run it i see this message:[/B][/COLOR]
[I]
Could not send command to scanner. Check scanner's status.[/I]

[COLOR=Blue]**after command sane-find-scanner:**[/COLOR]
[I]found USB scanner (vendor=0x04b8, product=0x083a) at libusb:001:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.
[/I]
**[COLOR=Blue]and this message is result of scanimage command:[/COLOR]**
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

[COLOR=Blue]please help me.[/COLOR]

---

### Post by ellgor on 2010-03-17
Hi,

It takes a reboot or start it from a terminal with :

sudo iscan

Regards, Ellgor.

---

### Post by fered on 2010-03-17
Same result!

not solved...

---

### Post by sisco311 on 2010-03-17
Please post the output of:
```
cat /etc/sane.d/epkowa.conf
```
```
ls -al /dev/usb*
```
and
```
id
```

---

### Post by fered on 2010-03-17
[COLOR=Red]1-[/COLOR]
# epkowa.conf -- sample configuration for the EPKOWA SANE backend
# Copyright (C) 2004, 2008, 2009  Olaf Meeuwissen                
#                                                                
# See sane-epkowa(5), sane-usb(5) and sane-scsi(5) for details.  

# Detect all devices supported by the backend.
# If you don't have a SCSI device, you can comment out the "scsi"
# keyword.  Similarly for the other keywords.                                                                                                                                    
#                                                                                                                                                                                
usb                                                                                                                                                                              
0x04b8 0x083a                                                                                                                                                                    
#scsi                                                                                                                                                                            


# For any USB scanner not known to the backend (yet), you may, at your
# own peril(!!), force the backend to recognise and use it via libusb.
# You can do so by the following configuration command:
#
#   usb <USB vendor ID> <USB product ID>
#
# SEIKO EPSON's USB vendor ID is '0x04b8' (without quotes).  In order
# to find the USB product ID, use lsusb(1).
# A sample configuration for the Epson Perfection 1650 (Epson GT-8200),
# which has a product ID of 0x0110, would look as follows:
#
#usb 0x04b8 0x0110


# For SCSI devices not detected, you can add an entry like:
#
#   scsi EPSON GT-20000
#
# where the GT-20000 bit corresponds to the SCSI model information as
# shown in the output of dmesg(1) or in the /var/log/kern.log file.


# Network attached devices may be made to work by first installing the
# (non-free) iscan-network-nt package and then adding configuration lines
# as per information below.
#
# For each network attached device, you must add an entry as follows:
#
#   net <IP-address|hostname> [port-number]
#
# Ask your network administrator for the device's IP address or check
# for yourself on the panel (if it has one).  The port-number is very
# optional and defaults to 1865.
# Note that network attached devices are not queried unless configured
# in this file.
#
# Examples:
#
#net 192.16.136.2 1865
#net 10.0.0.1
#net scanner.mydomain.com


[COLOR=Red]2-[/COLOR]
lrwxrwxrwx 1 root root      7 2010-03-17 14:39 /dev/usblp0 -> usb/lp0
crw-rw---- 1 root root 253, 0 2010-03-17 18:08 /dev/usbmon0
crw-rw---- 1 root root 253, 1 2010-03-17 18:08 /dev/usbmon1
crw-rw---- 1 root root 253, 2 2010-03-17 18:08 /dev/usbmon2
crw-rw---- 1 root root 253, 3 2010-03-17 18:08 /dev/usbmon3
crw-rw---- 1 root root 253, 4 2010-03-17 18:08 /dev/usbmon4
crw-rw---- 1 root root 253, 5 2010-03-17 18:08 /dev/usbmon5

/dev/usb:
total 0
drwxr-xr-x  2 root root     60 2010-03-17 14:39 .
drwxr-xr-x 18 root root   4220 2010-03-17 16:28 ..
crw-rw----  1 root lp   180, 0 2010-03-17 14:39 lp0


[COLOR=Red]3-[/COLOR]
uid=1000(ali) gid=1000(ali) groups=4(adm),20(dialout),24(cdrom),46(plugdev),104(lpadmin),114(admin),117(sambashare),1000(ali)

---

### Post by sisco311 on 2010-03-17
Add your user to the lp gruop:
```
sudo gpaswd -a **username** lp
```
replace usrname with your login name.

Edit the /etc/sane.d/epkowa.conf file:
```
gksu gedit /etc/sane.d/epkowa.conf
```

to look like this:
```

# epkowa.conf -- sample configuration for the EPKOWA SANE backend
# Copyright (C) 2004, 2008, 2009 Olaf Meeuwissen 
# 
# See sane-epkowa(5), sane-usb(5) and sane-scsi(5) for details. 

# Detect all devices supported by the backend.
# If you don't have a SCSI device, you can comment out the "scsi"
# keyword. Similarly for the other keywords. 
# 
**usb 0x04b8 0x083a**
**usb /dev/usb/lp0** 
#scsi
...

```

Log out and log back in.

---

### Post by fered on 2010-03-17
and same message:

could not send command to scanner.

---

### Post by sisco311 on 2010-03-17
> **fered said:**
> and same message:

could not send command to scanner.

Did you try to unplug the scanner & plug it back in or reboot?

---

### Post by fered on 2010-03-19
Yes

---

### Post by fered on 2010-03-20
help me please!

---

### Post by freecode99 on 2010-03-26
Are you running 64 or 32 bit Ubuntu? If you are running 64 bit, I built a DEB for that as it was not supplied by Epson on their site. 

Also, are you connected directly to a USB port on the PC, or through a hub?

Just trying to help here.

---

### Post by freecode99 on 2010-03-26
Sorry, should have looked at the thread title I suppose.

Here's how you can do this yourself:

1) locate the downloaded iscan-*.i386.deb file on your computer
2) move that to your home folder:

mv iscan-*.i386.deb ~/username/

Where username is your user name in the system.

3) Make a directory for the file:

mkdir iscanx64

4) Change to that directory:

cd iscanx64

5) Make a DEBIAN directory below that directory

mkdir DEBIAN

6) Change back to your home directory:

cd ~

7) Take the iscan-*.i386.deb file and extract it:

sudo dpkg-deb --extract iscan-*.i386.deb iscanx64

8) Extract the control file next:

sudo dpkg-deb --control iscan-*.i386.deb iscanx64/DEBIAN

9) Edit the control file:

sudo gedit ./iscanx64/DEBIAN/control

10) Find the line that begins with "Architecture:" and replace the "i386" with "all"
      Code:

      Architecture: all

11) Delete the line that begins with "Original-Maintainer: xxxx" as this will prevent you from seeing an error when the package is built (not necessary, but correct - you could add your name - but that's not correct either)

12)  Click Save and close gedit.

13) Type the following to build the package.

      sudo dpkg-deb --build iscanx64

14) Click on the new iscanx64.deb package to install it or type the following:

      sudo dpkg -i ./iscanx64.deb

T%his will install the package onto your 64 bit system. You should logout and log back in to see the new iscan item under your graphics menu. You should be able to run it at this point.

HTH.

---

### Post by fered on 2010-03-27
I got the source files and ran "make" and "make-install" and iscan installed on my system and not work correctly. 
U mean that I should reinstall iscan in that way you said to work?

---

### Post by fered on 2010-04-03
[SIZE=6]**[COLOR=Red]I can't use scanner and no one help me![/COLOR]**[/SIZE]

---

### Post by Pug226 on 2010-04-19
What is the output of ```
scanimage -L
```
and the same as root ```
sudo scanimage -L
```

I had a similar problem and post 3 ([here]("http://www.linuxquestions.org/questions/linux-hardware-18/only-can-scan-as-root-usb-scanner-and-ubuntu-8-10-a-721079/")) fixed it for me. Turns out the permissions weren't set correctly by udev. scanimage -L returned different results when ran as root.

---

### Post by hic3456 on 2011-05-28
Not sure this is still an issue here, but I had a similar problem and solved it "trivially" (ie, I wasted half an hour figuring things out).

It looks as if iscan.conf in /etc/sane.d/dll.d/ still points to this 'mythical' epokwa.conf (I found references everywhere, but it appears the folks at Avaya have dropped it?) which is no longer installed in /etc/sane.d

In that folder, however, there is an epson2.conf (and an epson.conf one) that works just fine for me (YMMV):

```
~$ sudo cat /etc/sane.d/dll.d/iscan 
# iscan -- enables the SANE backend(s) required
# Any changes to this file will be lost when upgrading iscan.

epkowa

```

Note the fact that changing this file will cause grief if/when you upgrade iscan.  Instead of editing it, do this:

```
~$ sudo cp /etc/sane.d/epson2.conf /etc/sane.d/epkowa.conf
~$ cat /etc/sane.d/epkowa.conf
# epson2.conf
#
# here are some examples for how to configure the EPSON2 backend

# SCSI
# scsi EPSON
# for the GT-6500:
# scsi "EPSON SC"

# Parallel port
#pio 0x278
#pio 0x378
#pio 0x3BC

# USB
# usb

# For libusb support for unknown scanners use the following command
# usb <product ID> <device ID>
# e.g.:
# usb 0x4b8 0x110

# Network
# 
net 192.168.1.223
# net autodiscovery

```

Note I've set an explicit IP there (the autodiscovery did not seem to work, but you may want to give it a shot): if you have DHCP enabled on your printer, you will have to set the address manually via the printer's control panel (takes 30 seconds).

Let me know whether it works for you.

[http://codetrips.blogspot.com](http://codetrips.blogspot.com)

---

### Post by queen062009 on 2011-06-05
Hi, I am new to the command lines, so did not find my way through them.

I found a lot of information in the Epson Printer User Manual ([http://linux.avasys.jp/drivers/pips/doc/3.8.0-2/UsersManual.en.txt](http://linux.avasys.jp/drivers/pips/doc/3.8.0-2/UsersManual.en.txt)) and also the Note:[INDENT]'Do not connect the printer yet. Connect the printer after installing the software. If you connect the printer and it is registered to CUPS before installing the software, once uninstall the printer.'[/INDENT]However, did not understand too much of it and even though I forgot to disconnect the printer, after going through downloading and installing the packages for an Epson TX120 scanner, it was simply working.

Before going into Scanner specifics I opened the Synaptic Package Manager and checked for 'Sane' to make sure it is installed. 
Then I downloaded the necessary 'Iscan data' installing those via Ubuntu's Software Center.
Secondly I downloaded the 'core package' and also installed that via Ubuntu's Software Center.

You can tick your CX9300F and enter the details of your OS here:
[http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)

Assuming that you use Ubuntu 11.04 I proceeded to the next page and CX9300F is listed here:
[http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do)
Scroll down to section for the scanner and under:
 **Download for Epson Stylus CX9300F/CX9400Fax/DX9400F data package**

 ... choose the data package you need. Download it and open it with the Ubuntu's Software Center.

Thereafter go to:
 **Download for Epson Stylus CX9300F/CX9400Fax/DX9400F core package**

 ... choose the data package you need. Download it and open it with the Ubuntu's Software Center.

NO guarantee that it will work for you... but try it, it won't take long.

---

