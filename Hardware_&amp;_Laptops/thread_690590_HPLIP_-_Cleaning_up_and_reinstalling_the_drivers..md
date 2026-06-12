---
title: "HPLIP - Cleaning up and reinstalling the drivers."
date: 2008-02-07
forum: Hardware &amp; Laptops
---

### Post by gwm on 2008-02-07
Hi,
Please can anyone help me with the reinstallation of these drivers. I seem to have missed something. Where does the CUPS find the printer settings? Are they kept in the ppd files and where are they kept?

I have an HP F380 scanner printer connected to a dual boot system running Gutsy. I have been having trouble with color printing. Once I had set the printer to print in gray scale, It refused to (I couldn't get it to) print in color again. That is, if I used Open Office or Firefox. However, if I exported to a pdf file, then I could print in color. This indicates software problems with the settings somewhere.

To try and fix it, I deleted the printer and totally removed all the hplip related drivers I could find. Then I reinstalled everything and redefined the printer. Now I cant print anything, not even get gray scale, only lots of flickering lights on the printer.

I also installed HPLIP toolbox. It insists that the printing has completed. When I initially run up the tool box, it takes ages and ages, to find the printer. Yet the setup wizard finds it instantly.

I've looked everywhere I can think of without success.  Dual booting to windows finds a working printer, so all the hardware and connections and all are fine.

Please can anyone help?

Billy Mes:popcorn:

---

### Post by ItalOz on 2008-02-11
same (i think) problem here, I've installed HPLIP because I wanted to see if I could get a better driver for the HP printers we have got here at office.

When I installed it the 1st time it found me all the connected (network) printer, I installed one and everything seemed to have gone fine.

Then I run again ```
sudo hp-setup
```

and it could not find me any network printers. The Ubuntu printing tool finds them all within seconds.
The HP tool does not find a printer anymore.

Only thing I did not try yet is to uninstall and re-install.

Any idea out there?

---

### Post by gwm on 2008-02-26
I have a similar problem with the Windows driver for the same device. If the paper jams and then I clear it, the print queue and all seem to be happy, yet the MS version of HPLIP hangs. The only way I have found to get it going again, is to reboot.
Microsoft have a similar bug with their COM+ code. When it goes wrong, you have to reinstall Windows. I'm busy with that on one of our work machines at the moment. I guess Linux is not immune to these things either.
Since no one has yet been able to make any concrete suggestions, I suppose I will have to save my things as best I can and go through weeks of reinstalling and setting up all over again. I feel it is not a  good show when a printer driver can do this to one's system.

:popcorn:

---

### Post by 11hjpphty76lkjj on 2008-02-26
Please run hp-check -t and post the output.

Thanks!

Aaron

---

### Post by gwm on 2008-02-27
Hi,

billy@puer:~$ hp-check -t
bash: hp-check: command not found
billy@puer:~$ 

Which directory must I be in? I saw something about it on the sourceforge site but can't find it again and I don't know what the equivalent to "dir /s" is in Linux.

Billy

---

### Post by 11hjpphty76lkjj on 2008-02-27
This means you are using the pre-packaged hplip that comes with ubuntu. Which is good to.  Please run the printingbuginfo script--link in my sig. and post the output.

Thanks!

A

---

### Post by gwm on 2008-02-29
Hi,
Please help me. I don't understand the jargon. I've come from UNIVAC mainframes down to a host of different mini computers then DOS and Windows. I don't have a Unix background and so far haven't got as far as developing anything in Linux, so trying to decipher the request is sheer guesswork.

Guess 1, You asked me ro run a script. I guess I must type [Bsh][/B] followed by the script name.
Guess 2. [Bmy sig][/B]? Is that my home directory or what?

I'm not trying to be difficult. If I knew all this stuff, I probably wouldn't need help.

---

### Post by 11hjpphty76lkjj on 2008-02-29
gwm,

Please go to this url:

[https://wiki.ubuntu.com/PrintingBugInfoScript](https://wiki.ubuntu.com/PrintingBugInfoScript)

And follow the directions about posting the printingbuginfo script output.

and by "link in my sig" I mean--the URL to the printingbuginfo script wiki is in my signature, below my name--simply click on Printingbuginfo script.

Aaron

---

### Post by gwm on 2008-03-05
Thanks Aaron,
I've done as instructed. I think I've attached the output but I don't see any feedback here telling me about it, so I'm also pasting the contents of the file here. It indicates that I've tried to set the printer up as a Deskjet 3810. That is simply the latest in my series of attempts to get something to work. I've been to the suggested technical data site but none of the drivers for the dj3600 class are offered to me when I change the model of the printer.

ProblemType: printingbuginfo v2.0: printingbug+localusb ([https://wiki.ubuntu.com/PrintingBugInfoScript](https://wiki.ubuntu.com/PrintingBugInfoScript))
CupsConfiguredDevices:
 device for Deskjet_F380: hp:/usb/Deskjet_F300_series?serial=CN6A5G54ZX04KH
 device for PDF: cups-pdf:/
CupsConfiguredPPDs:
 Deskjet_F380: HP DeskJet 3810 - CUPS+Gutenprint v5.0.1 Simplified
 PDF: Generic PDF file generator
Date: Wed Mar  5 20:09:23 2008
DesktopEnvironment: GNOME
DistroRelease: Ubuntu 7.10
EtcPapersize: a4
InstalledPrintingPackages:
 ii  cupsys                   1.3.2-1ubuntu7.5         Common UNIX Printing System(tm) - server
 ii  cupsys-driver-gutenprint 5.0.1-0ubuntu8           printer drivers for CUPS
 ii  foo2zjs                  20070625-0ubuntu1.1      Support for printing to ZjStream-based printers
 ii  foomatic-db              20070919-0ubuntu3        OpenPrinting printer support - database
 ii  foomatic-db-engine       3.0.2-20070719-0ubuntu4  OpenPrinting printer support - programs
 ii  foomatic-filters         3.0.2-20070719-0ubuntu1  OpenPrinting printer support - filters
 ii  ghostscript              8.61.dfsg.1~svn8187-0ubu The GPL Ghostscript PostScript/PDF interpreter
 ii  hpijs                    2.7.12+2.7.12-0ubuntu2~g HP Linux Printing and Imaging - gs IJS driver (hpijs)
 ii  hplip                    2.7.12-0ubuntu2~gutsy1   HP Linux Printing and Imaging System (HPLIP)
 ii  libgnomeprint2.2-0       2.18.2-0ubuntu1          The GNOME 2.2 print architecture - runtime files
 ii  min12xxw                 0.0.9-1build1            Printer driver for KonicaMinolta PagePro 1[234]xxW
 ii  openprinting-ppds        20070919-0ubuntu3        OpenPrinting printer support - PostScript PPD files
 ii  pnm2ppa                  1.12-16                  PPM to PPA converter
 ii  pxljr                    1.1-0ubuntu1             Driver for HP's Color LaserJet 35xx/36xx color laser printers
 ii  splix                    1.0.1.1-0ubuntu2         Driver for Samsung's SPL2 (bw) and SPLc (color) laser printers
 ii  system-config-printer    0.7.75+svn1653-0ubuntu2  Printer configuration GUI
Locale: LANG=en_ZA.UTF-8, LC_CTYPE=en_ZA.UTF-8, LC_PAPER=en_ZA.UTF-8
Uname: Linux puer 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux
UsbPrinterDevices: 
UsbPrinterIEEE1284Id: 
UsbPrinterKernelModules:
 usblp                  15104  0 
 usbcore               138632  8 usblp,snd_usb_audio,snd_usb_lib,usbhid,gspca,ehci_hcd,uhci_hcd
lsusb:
 Bus 005 Device 001: ID 0000:0000  
 Bus 002 Device 002: ID 0ac8:0302 Z-Star Microelectronics Corp. ZC0302 WebCam
 Bus 002 Device 001: ID 0000:0000  
 Bus 004 Device 001: ID 0000:0000  
 Bus 003 Device 001: ID 0000:0000  
 Bus 001 Device 006: ID 03f0:5511 Hewlett-Packard 
 Bus 001 Device 004: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
 Bus 001 Device 001: ID 0000:0000

---

### Post by gwm on 2008-03-14
Solved,  :lolflag:
by brushing everything aside. I downloaded the latest run file from lauchpad. However, I saved it to a FAT32 partition. Don't do that When I ran it, it unpacked a help file (sot of after the event) amongst other things, even though the install failed.

I realized my mistake, moved the run file to my desktop and ran it from there. The run file script did an excellent job. It installed the needed compilers and everything automatically, then made and installed HPLIP.

The installation recognized my printer as an F300 and drove it well. There is no option for an F380. The other UBUNTU Pc on my network found the printer after a reboot and seems to be using the new software too. Very nice!!  :KS

A word of caution regarding a shared printer. First get your router up and running (I unplug mine during electrical storms - crude but effective lightning protection). Next switch on the printer. Third, start up the printer server Pc. Finally, start up the client Pc. If you do it in a different order, the client doesn't see the printer.

:guitar:

---

