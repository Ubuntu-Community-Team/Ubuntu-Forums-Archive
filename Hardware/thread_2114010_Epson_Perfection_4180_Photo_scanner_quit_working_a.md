---
title: "Epson Perfection 4180 Photo scanner quit working after recent update"
date: 2013-02-08
forum: Hardware
---

### Post by gtyurkon on 2013-02-08
I love Linux and have used it since 1995 but I'm just about ready to go back to Windows. I am on 10.04 (old but still supported I think) and I run updates as they come available. Bad idea I guess because all the updates do is break things. Plus at age 70, I'm not into debugging anymore.
Anyway, my scanner worked fine for years but after a recent update it's disappeared. 
sane-find-scanner produces the following:
found USB scanner (vendor=0x04b8 [EPSON], product=0x0118 [EPSON Scanner]) at libusb:001:002

However, scanimage -L produces:
No scanners were identified

I use vuescan (nice program), but it relies on Ubuntu drivers for access to scanner so it no longer works.
Does anyone know of recent changes that would cause this?
I may take the plunge with 12.04, but I expect that will just break even more stuff. :-(

---

### Post by pdc on 2013-02-11
I am not sure if you have the Epson drivers installed ..

from here

[http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)

if one enters 4180, you get 2 options: 

gcc 3.2 and 3.3

or gcc 3.4 and later 

.........I don't know which is right for you

I see the package comes down for 3.4 as [COLOR="SeaGreen"]iscan_2.10.0-1.tar.gz
[/COLOR]
and archive manager should manage it 

....to run....... in a terminal one types

> [COLOR="Red"]iscan[/COLOR]

---

### Post by jklex on 2013-02-11
I have the same problem but with a new attempt to install an Epson 3170 Photo scanner on 10.04.  I downloaded and installed the pkgs from the new site mentioned in the reply.  I downloaded the version gcc 3.4 .rpm files.  I had to convert them to .deb but they installed OK and the downloaded files all got put in the correct folders and the new library files were installed.  Still no device detected although it appears in the queries for devices such as lsusb.  I then modified the epson2.conf and the new epkowa.conf files to show the device settings.  Still no device detection in the various scanner programs I have installed: simplescan, xsane, iscan or gimp.  If you have better luck with the tar file install please let me know.

---

### Post by jklex on 2013-02-11
> **jklex said:**
> I have the same problem but with a new attempt to install an Epson 3170 Photo scanner on 10.04.  I downloaded and installed the pkgs from the new site mentioned in the reply.  I downloaded the version gcc 3.4 .rpm files.  I had to convert them to .deb but they installed OK and the downloaded files all got put in the correct folders and the new library files were installed.  Still no device detected although it appears in the queries for devices such as lsusb.  I then modified the epson2.conf and the new epkowa.conf files to show the device settings.  Still no device detection in the various scanner programs I have installed: simplescan, xsane, iscan or gimp.  If you have better luck with the tar file install please let me know.
A few minutes ago I found I could get the Epson 3170 to work in simple-scan if I ran it as sudo but not every time.  Out of four attempts in sudo I got it to work three times.  ODD!

---

### Post by jklex on 2013-02-11
> **jklex said:**
> A few minutes ago I found I could get the Epson 3170 to work in simple-scan if I ran it as sudo but not every time.  Out of four attempts in sudo I got it to work three times.  ODD!
OK now it is fixed.  I found I had to correct the permissions on my basic admin acct to allow saned privileges and to add my scanner to the sane rules file.  Here is the link for the instructions:  [https://help.ubuntu.com/community/SettingScannerPermissions](https://help.ubuntu.com/community/SettingScannerPermissions)

 It was necessary to check the box next to my acct name.  I can now run the Epson 3170 in simple-scan and xsane from by basic acct without having to sudo.

---

### Post by gtyurkon on 2013-02-19
jklex, thanks for your input. I will try this after installing 11.10. But I don't understand why my scanner quit, after working for something like several years. I vaguely remember doing this back then. An update must have undone something. Thanks for your help.

---

### Post by gordintoronto on 2013-02-19
Might I suggest that you go to 12.04 rather than 11.10? Both 10.04 and 11.10 will expire in two months, but 12.04 will be supported until 2017.

---

### Post by gtyurkon on 2013-02-27
Thanks all for the help. I got my Epson Perfection 4180 Photo to work after a new install of Xubuntu 12.04 (I have an old machine) by doing what I've described below. I doubt this will help anyone, but just in case, I thought I'd post it.

Getting vuescan (great scanner program from hamrick.com) to work with Epson Perfection 4180 Photo
System: 32-bit Xubuntu 12.04 

I downloaded RPMs from [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)
I used "4180 photo" in the search box. The 2 RPMs (see below) were converted to deb files with alien.
(Both iscan and iscan-plugin)

In a terminal, to create the deb files:
sudo alien --scripts iscan-2.10.0-1.c2.i386.rpm 
sudo alien --scripts iscan-plugin-gt-f600-1.0.0-1.c2.i386.rpm 

Then:
sudo dpkg -i iscan_2.10.0-2_i386.deb 
sudo dpkg -i iscan-plugin-gt-f600_1.0.0-2_i386.deb 

Note:
Without "--scripts" option above, vuescan recognized 4180, but Preview and Scan returned nothing.
With "--scripts", everything worked.

The /etc/sane.d/epkowa.conf file from Epson worked as is.

The only remaining issue to get vuescan working was a permissions problem. I created a file called 99-epson4180.rules which I placed in the /etc/udev/rules/ directory. Naming conventions are important here. There should be a readme in the same directory. My file contained the following:

SUBSYSTEM!="usb_device", ACTION!="add", GOTO="epson4180_rules_end"

# This file should be in /etc/udev/rules.d/99-epson4180.rules as owner/group root, permissions 644
# Epson Perfection 4180 Photo
# The idVendor and idProduct were determined by doing a lsusb command with the scanner turned on.
# For example, my lsusb showed a line for the Epson containing "ID 04b8:0118"
ATTR{idVendor}=="04b8", ATTR{idProduct}="0118", MODE="0666", OWNER="root", GROUP="root"

LABEL="epson4180_rules_end"

---

### Post by pdc on 2013-02-27
well done; enjoy

an alternative to converting rpm to .deb with alien could have been to install the generic iscan_2.10.0-1.tar.gz

you did very well mastering the permissions issues with vuescan; well done

---

