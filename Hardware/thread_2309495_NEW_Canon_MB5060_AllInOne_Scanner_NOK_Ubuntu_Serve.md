---
title: "NEW Canon MB5060 AllInOne Scanner NOK Ubuntu Server 10.10 Client 14.04"
date: 2016-01-11
forum: Hardware
---

### Post by donnywood-studio on 2016-01-11
HI folks

I just got a new Canon MB5060 and trying to get scanner working via  xsane which is not quite working. 

My config is Ubuntu Server ( 10.10 ) and clients  14.04 LTS,WIN 10 Pro and Canon Network All-In-One MB5060.

I configured the MB5060 on the server as network printer using cnijfilter2-5.00-1-deb package comes from Canon and it works fine ( printing anyway on ubuntu clients )

I can detect the scanner on 10.10 but xsane does not see it.  

Is there any other tool beside sane-find-scanner or scaneimmage -L to probe the USB port . ?

Below Some output on commands ran  & install script from Canon ( dmesg, sane-find-scanner & scanimage -L)

 =========================================================#
#  Connection Method
#=========================================================#
 1) USB
 2) Network
Select the connection method.[1]2

Searching for printers...


#=========================================================#
#  Select Printer
#=========================================================#
Select the printer.
If the printer you want to use is not listed, select Update [0] to search again.
To cancel the process, enter [Q].
-----------------------------------------------------------
 0) Update
-----------------------------------------------------------
T[COLOR=#ff0000]arget printers detected (MAC address  IP address)
1) Canon MB5000 series (F8-0D-60-34-16-23 192.168.0.19)[/COLOR]
-----------------------------------------------------------
Currently selected:[1] Canon MB5000 series (F8-0D-60-34-16-23 192.168.0.19)

The 14.04 clients prints fine to the print server 10.10.

I have now MB5060 conencted via USB to also get xsane working and I can detect on the server but dies not get detceted on xane .

below output from sane-find-scanner , dmesg and scanimage -L from the server 10.10.    I also loaded the scanner  driver from Canon scangearmp2-3.00-1-deb.

#######################################
##############
director@director-OptiPlex-GX620:~/Downloads/scangearmp2-3.00-1-deb$** uname -a**
Linux director-OptiPlex-GX620 2.6.35-32-generic #67-Ubuntu SMP Mon Mar 5 19:35:26 UTC 2012 i686 GNU/Linux
director@director-OptiPlex-GX620:~/Downloads/scangearmp2-3.00-1-deb$ **dmesg|tail -6**
[595864.731453] usb 1-1: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
[595864.731535] usb 1-1: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
[595864.744077] usblp0: removed
[595864.751819] usblp1: removed
[COLOR=#ff0000][595864.757000] usblp0: USB Bidirectional printer dev 33 if 1 alt 0 proto 2 vid 0x04A9 pid 0x1776
[595864.758250] usblp1: USB Bidirectional printer dev 33 if 2 alt 0 proto 2 vid 0x04A9 pid 0x1776[/COLOR]
director@director-OptiPlex-GX620:~/Downloads/scangearmp2-3.00-1-deb$ ./install.sh
[sudo] password for director: 
==================================================

ScanGear MP
Version 3.00
Copyright CANON INC. 2007-2014

==================================================
Command executed = sudo dpkg -iG ./packages/scangearmp2_3.00-1_i386.deb
(Reading database ... 211655 files and directories currently installed.)
Preparing to replace scangearmp2 3.00-1 (using .../scangearmp2_3.00-1_i386.deb) ...
Unpacking replacement scangearmp2 ...
Setting up scangearmp2 (3.00-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Installation has been completed.
director@director-OptiPlex-GX620:~/Downloads/scangearmp2-3.00-1-deb$ **sudo sane-find-scanner |grep Canon**
[COLOR=#ff0000]found USB scanner (vendor=0x04a9 [Canon], product=0x1776 [MB5000 series]) at libusb:001:033[/COLOR]
director@director-OptiPlex-GX620:~/Downloads/scangearmp2-3.00-1-deb$ sudo scaneimage -L
sudo: scaneimage: command not found
director@director-OptiPlex-GX620:~/Downloads/scangearmp2-3.00-1-deb$ **scanimage -L**

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
director@director-OptiPlex-GX620:~/Downloads/scangearmp2-3.00-1-deb$

rgds
don

---

