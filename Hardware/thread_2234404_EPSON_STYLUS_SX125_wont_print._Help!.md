---
title: "EPSON STYLUS SX125 wont print. Help!"
date: 2014-07-14
forum: Hardware
---

### Post by Silotimtar on 2014-07-14
Specs: Kubuntu 14.04, Os type 32bit, Epson stylus sx125 -usb connected (low ink level - red light on)

I´ve downloaded  > epson-inkjet-printer-n10-nx127_1.0.1-1lsb3.2_i386.deb from the epson site
installed ok (directory /opt/epson.... created)
(I´ve also installed the scanner´s .deb files)
I tried to install the printer in different ways (1. from system settings and 2. using  the CUPS frontend. selecting the printer from 1. the dropdown list and 2. manually) (thats 4 installations
I got the following details about the printer: 

[TABLE]
[TR]
[TH]Description:[/TH]
[TD]EPSON Epson Stylus SX125[/TD]
[/TR]
[TR]
[TH]Location:[/TH]
[TD][/TD]
[/TR]
[TR]
[TH]Driver:[/TH]
[TD]Epson Stylus SX125 Series - epson-inkjet-printer 1.0.1-1lsb3.2 (Seiko Epson Corporation LSB 3.2) (color, 2-sided printing)[/TD]
[/TR]
[TR]
[TH]Connection:[/TH]
[TD]usb://EPSON/Stylus%20SX125?serial=MDMZ017604%20%20%20%20%20%20%20%20&interface=1[/TD]
[/TR]
[TR]
[TH]Defaults:[/TH]
[TD]job-sheets=none, none media=iso_a4_210x297mm sides=one-sided[/TD]
[/TR]
[/TABLE]
So the printer seems to be active, but 
as many times as I tried to print a Test page (or something else) the same thing happens:

¨Access log:

localhost - - [14/Jul/2014:21:00:42 +0300] "POST /printers/Epson-Stylus-SX125 HTTP/1.1" 200 423 Print-Job successful-okseems to be ok, and
**Status**
Processing - "Processing page 1..."


This seems to last forever everytime I try it, and thus I have to abort the job

CUPS frontend log page:
  
[TABLE="class: list"]
[TR]
[TD][Epson-Stylus-SX125]("http://localhost:631/printers/Epson-Stylus-SX125")-20[/TD]
[TD]Name Unknown[/TD]
[TD]User Withheld[/TD]
[TD]Size 1k[/TD]
[TD]Pages Unknown[/TD]
[TD]State processing since
Mon 14 Jul 2014 09:00:42 PM EEST 
*"Processing page 1..."*[/TD]
[/TR]
[/TABLE]

I´ve tried 4 times to reinstall, every time the same problem. (Before each installation, printer was discon´ed, power off, uninstalled, drivers uninstalled too)

If anyone can hwelp I&#314;l be much oblidged.
(Hope it isn´t due to the low ink level or I´ll go hang myself)

---

### Post by pdc on 2014-07-14
sorry to hear of your troubles;

you seem a very organised person; 

here is a link to the Ubuntu debugging wiki for printing: [https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems)

if you work through that and see if it helps?

________

towards the end it points out there is a Troubleshooting Wizard from either your printing menu item or > [COLOR="#FF0000"]system-config-printer[/COLOR]

---

