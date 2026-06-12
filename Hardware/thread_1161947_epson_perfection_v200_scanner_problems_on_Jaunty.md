---
title: "epson perfection v200 scanner problems on Jaunty"
date: 2009-05-17
forum: Hardware
---

### Post by boddhisatva on 2009-05-17
I have a problem with this scanner with each upgrade, and so do a few other people (see: [http://ubuntuforums.org/showthread.php?p=7295395#post7295395]("http://ubuntuforums.org/showthread.php?p=7295395#post7295395") for Intrepid). 
I install iscan, which doesn't see the scanner, neither does xsane. Lsusb sees it, though. When I run "sudo iscan" from terminal, the application recognizes the scanner and runs OK (although it works much more slowly for some reason, with frequent pauses). Has anyone got this scanner working on Jaunty?

---

### Post by 2CV67 on 2009-05-18
As I said, I have not tried Jaunty yet, so can't help directly.

I did find a couple of items on the Avasys message board about problems with Jaunty, you might want to look there?

[http://www.avasys.jp/english/linux_e/bbs_scan.html](http://www.avasys.jp/english/linux_e/bbs_scan.html)

I had a lot of problems with that site, but one message 
[http://www.avasys.jp/cgi-bin/lx/bbs/en/scanner-bbs/hyperbbs.cgi?mode=view;Code=5094](http://www.avasys.jp/cgi-bin/lx/bbs/en/scanner-bbs/hyperbbs.cgi?mode=view;Code=5094)
said:> I tried everything to get my brand new Epson TX800FW scanning to Linux (Ubuntu 9.04).
The iscan deb package wouldn't install so I managed to compile iscan 2.19.0 from
source after installing a heap of required miscellaneous packages but iscan just
refused to recognise the scanner.
("Could not send command to scanner. Check the scanner's status")

I finally resorted to running an strace on iscan and found that it was looking for
the epkowa libraries in /usr/local/lib whereas the iscan "make install" had installed
the libraries in /usr/local/lib/sane.

Setting the LD_LIBRARY_PATH to /usr/local/lib/sane fixed my problem.

Note that this was after adding a line "epkowa" to /etc/sane.d/dll.conf

I also had to add the udev rule for sane to allow members of the scanner group to
access the device. To do this, I created /etc/udev/rules.d/45-libsane.rules and
added the single line:
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0844", MODE="664", GROUP="scanner"
The vender ID and product ID having been obtained from sane-find-scanner.
Then had to run /etc/init.d/udev restart.

Hope you get this fixed before I get to Jaunty!

---

### Post by boddhisatva on 2009-05-19
2CV67, thanks a lot for staying interested? :). How did you come across this new thread?
I'm afraid I don't know how to set the path as indicated in the post quoted by you - still lacking some Linux skills... (I followed the link to Avasys, but couldn't post my question there as the site seems to be working erratically.)
By the way, the SCANNER group is often mentioned in the posts. Problem is, I don't even have that group, only SANED.

---

### Post by boddhisatva on 2009-05-23
They've posted new drivers for the scanner at avasys.jp. There's even a ready-made .deb package. There's a problem with dependencies: libltdl3 is not present in 9.04 repository (or in 8.10 for that matter), but you can download it here: [http://packages.ubuntu.com/hardy/i386/libltdl3/download]("http://packages.ubuntu.com/hardy/i386/libltdl3/download")
The driver is still not working without sudo, but at least it's now working A LOT faster (it worked REALLY slowly in 9.04 on the old driver) - it's even faster than the old driver on 8.10. So there's hope and (this is to 2CV67 and others) there's a reason for switching to 9.04 - once you find out how to get round the sudo problem of course :)
Typing sudo before starting GIMP (from which I've always scanned anyway) is not such a big problem for me, but of course it would be nice to have it running without additional hassle (such as having the scanned images saved with 'root privileges', which I then have to change).

---

### Post by boddhisatva on 2009-05-23
HEHE - IT LOOKS LIKE I FORGOT TO DO ONE THING - REBOOT! :D
NOW IT'S WORKING WITHOUT SUDO OR ANY OTHER TRICKS. 
I meddled with the system a bit in the meantime, but probably it would have run fine if I had rebooted straight after installing the new driver. I hope I haven't compromised my system security with those unnecessary tricks #-o
Anyway, time to scan away!
:popcorn:

---

### Post by 2CV67 on 2009-05-24
Thanks for that encouraging & useful information.

I will still wait a couple of months before switching to Jaunty, but I feel happier about it now.

Bring back the "Thank You" button!

---

### Post by ziggzagg on 2009-06-20
Hi guys,

I also had problems to make this scanner work under Jaunty 64, but after reading soooooo many posts I was able to figure out what to do to finally make it work. I wrote this little step by step setup guide and hope it will aslo be usefull for everyone who is having a hard time with the Epson V200. It was much easier too set it up in Mandriva 2009.1 ;-)


1. Download driver from [www.avasys.jp/english](www.avasys.jp/english)	

- Click on Driver Download under Linux Driver
- Click on Scanner under Download
- Enter these informations:
	*Model*: Perfection V200 PHOTO
	*Distribution*: Ubuntu
	*Distribution version*: 9.04
	*Your country/region*: &#8220;your own country&#8221;
	*Connection environment for using scanner*: Scan with local scanner
	*Location for the product*: Individuals(Graphic/mage)
- Click on Next
- Download these packages:
	iscan_2.20.0-6.ltdl7_i386.deb
	iscan-plugin-gt-f670_2.1.0-3_amd64.deb


2. Install packages


3. Create 45-libsane.rules in /etc/udev/rules.d and copy these lines so it looks that way:

# Epson Corp.|Perfection V200 Photo 
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="012e", MODE="664", GROUP="scanner"


4. Create epkowa.conf in /etc/sane.d and copy these lines so it looks that way:

# epkowa.conf &#8212; sample configuration for the EPKOWA SANE backend 
# Copyright (C) 2004  Olaf Meeuwissen 
# 
# See sane-epkowa(5), sane-scsi(5) and sane-usb(5) for details. 

# SCSI scanners can be configured simply by listing the path to the 
# device.  For example, if your system claims to have a /dev/scanner 
# SCSI device, all you have to do is uncomment the following line: 
# 
#/dev/scanner 
# 
# In the interest of maintainability, most installations would have 
# /dev/scanner sym-linked to the real SCSI scanner device node. 
# 
# An alternative way that works for many operating systems and is a 
# little bit more generic, is to have the backend probe for your SCSI 
# scanner with the following configuration command: 
# 
scsi EPSON 

# On systems with libusb, the following line is sufficient to get the 
# backend to recognise your USB scanners.  It presumes, however, that 
# the scanner&#8212;more precisely, it&#8217;s USB product ID&#8212;is known to the 
# backend. 
# For all USB scanners that are officially supported by this backend, 
# this presumption is true.  A list of such scanners can be found in 
# sane-epkowa(5). 
# 
usb 

# For any USB scanner not known to the backend (yet), you may, at your 
# own peril(!!), force the backend to recognise and use it via libusb. 
# You can do so by the following configuration command: 
# 
#   usb <USB vendor ID> <USB product ID> 
# 
# SEIKO EPSON&#8217;s USB vendor ID is &#8216;0×04b8&#8242; (without quotes).  In order 
# to find the USB product ID, use lsusb(1) or, on Linux systems, peek 
# at the information in /proc/bus/usb/devices. 
# A sample configuration for the Perfection 1650 (GT-8200), which has 
# a product ID of 0×0110, would look as follows: 
# 
usb 0×04b8 0x012e 

# When not accessing your USB scanner via libusb, you may need to use 
# one of the configuration commands below or commands that are almost 
# the same.  These commands typically access the scanner via a kernel 
# scanner module. 
# 
#usb /dev/usb/scanner0 
#usb /dev/usbscanner0 
#usb /dev/uscanner0 
# 
# Linux had a scanner module until version 2.6.2.  As of version 2.6.3 
# libusb is your only option.  Linux&#8217; scanner module can be loaded via 
# the modprobe(8) command like so: 
# 
#   modprobe scanner vendor=<USB vendor ID> product=<USB product ID> 
# 
# If the scanner module already knows the vendor and product IDs, you 
# do not have to specify them.  If you want to have this done automa- 
# tically every time you boot, you can add the above line, except for 
# the modprobe command itself, to your /etc/modules file. 

# Although not tested with this backend, parallel port scanners should 
# be usable.  You can configure them as shown below, but I do not know 
# much about the details.  Information is welcome. 
# 
#pio 0×278 
#pio 0×378 
#pio 0×3BC


5. Modify dll.conf file in /etc/sane.d and add these lines so it looks that way:

# /etc/sane.d/dll.conf - Configuration file for the SANE dynamic backend loader 
# 
# On Debian systems, the dll backend will also look for pieces of configuration 
# in the /etc/sane.d/dll.d directory -- packages providing backends should drop 
# a config file similar to dll.conf in this directory. 
# 

# enable the next line if you want to allow access through the network: 
net 
abaton 
agfafocus 
apple 
avision 
artec 
artec_eplus48u 
as6e 
bh 
canon 
canon630u 
#canon_pp 
cardscan 
coolscan 
coolscan2 
#dc25 
#dc210 
#dc240 
dell1600n_net 
dmc 
epjitsu 
epson 
epson2 
epkowa 
fujitsu 
#gphoto2 
genesys 
gt68xx 
hp 
hp3900 
hpsj5s 
hp3500 
hp4200 
hp5400 
hp5590 
hpljm1005 
hs2p 
ibm 
leo 
lexmark 
ma1509 
matsushita 
microtek 
microtek2 
mustek 
#mustek_pp 
mustek_usb 
mustek_usb2 
nec 
niash 
pie 
pixma 
plustek 
#plustek_pp 
#pnm 
qcam 
ricoh 
s9036 
sceptre 
sharp 
sm3600 
sm3840 
snapscan 
sp15c 
#st400 
#stv680 
tamarack 
teco1 
teco2 
teco3 
#test 
u12 
umax 
#umax_pp 
umax1220u 
v4l


6. Go to System/Administration/Users and Groups

Click on Unlock and enter your password
Click on Manage Groups
Click on Add Group
Group name: scanner
Group ID: 124
Click ok then close

I am not sure about the group nember but 124 worked out for me!!


7. Plug your scanner and turn it on.


8. Start Xsane to see if it detects your scanner


Unfortunately for those of you who would like to use VueScan, the latest version (8.5.17) doesn't work with that way of setting up the scanner. When you start the program it displays this message:

VueScan found an Epson Perfection V200, but no Epson software for this scanner was found on your system. Try downloading a driver for this scanner from [www.avasys.jp/english](www.avasys.jp/english). See the VueScan Release Notes for more information. 

Press 'Close' to start using VueScan.

Does anyone can figure out how to fix this problem with VueScan?

---

### Post by boddhisatva on 2009-06-21
Thank for all the info, ziggzagg. Maybe you need to do all that on a 64 bit machine, on a 32 bit one you just need to install the new driver, and it works out of the box (after a reboot). At least it did for me.

---

### Post by ^_Pepe_^ on 2009-06-23
Hi.

I've installed Epson V200 drivers and worked quite straight, but I'm not able to enable quick buttons in the scanner

[http://ubuntuforums.org/showthread.php?t=1194970](http://ubuntuforums.org/showthread.php?t=1194970)

Can anybody help me?

Thanks
^_Pepe_^

---

### Post by boddhisatva on 2009-06-23
I don't think anybody has been able to do that #-o
I'm happy it's working out of the box with the new driver, I've never bothered about the buttons :)
But perhaps someone has gone that far and can offer some advice...

---

