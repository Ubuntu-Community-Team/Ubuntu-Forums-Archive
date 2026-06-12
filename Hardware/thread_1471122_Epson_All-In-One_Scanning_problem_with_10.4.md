---
title: "Epson All-In-One Scanning problem with 10.4"
date: 2010-05-03
forum: Hardware
---

### Post by blegs38552 on 2010-05-03
I have an Epson Artisan 810 All-In-One networked device. I was able to print "right out of the box" following installation of 10.4 (fresh, not update). 

Tried scanning using Simple Scan. It shows my device but when I tried to scan, I got an "unable to communicate with the scanner" message. Tried installing XSANE with the same result. In both cases, the device's control panel display was only half displayed and was flashing on and off. I had to power down and power back up to regain functionality. 

Anyone have a solution for this? Tried Epson's web site, but they do not actively support Linux O/s's.

---

### Post by sisco311 on 2010-05-03
Try iscan: [http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)

---

### Post by blegs38552 on 2010-05-03
> **sisco311 said:**
> Try iscan: [http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)

Thanks - will try and post my result for others to see.

---

### Post by blegs38552 on 2010-05-03
> **sisco311 said:**
> Try iscan: [http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)
Tried downloading iscan-network-nt_1.1.0-2_i386.deb. Got a message from Package Installer - Error: Dependency is not satisfiable: iscan (>= 2.21.0. Install Package button was greyed out. Tried download for both Ubuntu 9.10 and Ubuntu unknown.

---

### Post by prtsmgr on 2010-05-11
> **blegs38552 said:**
> Tried downloading iscan-network-nt_1.1.0-2_i386.deb. Got a message from Package Installer - Error: Dependency is not satisfiable: iscan (>= 2.21.0. Install Package button was greyed out. Tried download for both Ubuntu 9.10 and Ubuntu unknown.

Go back and download one at the bottom of the page labeled latest version:
[http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do)

iscan_2.24.0-4.ltdl7_i386.deb
or
iscan_2.24.0-4.ltdl7_amd64.deb

and after installation, edit /etc/sane.d/epkowa.conf by adding an entry for your printer's ip address like:
#
net 192.168.2.7

---

### Post by blegs38552 on 2010-05-11
> **prtsmgr said:**
> Go back and download one at the bottom of the page labeled latest version:
[http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do)

iscan_2.24.0-4.ltdl7_i386.deb
or
iscan_2.24.0-4.ltdl7_amd64.deb

and after installation, edit /etc/sane.d/epkowa.conf by adding an entry for your printer's ip address like:
#
net 192.168.2.7

Tried installing this for Epson Artisan 810. Launched XSANE and clicked on SCAN. Received the following message "Error During Read. Error during Device I/O". Scanner showed "Communication Error. Make Sure
Computer is Connected and Try Again"

---

### Post by prtsmgr on 2010-05-11
I have an Epson Artisan 810 as well.
I know it will not work with xsane.
You will need to downlaod and install *Image Scan! for Linux* from the links I provided in order to get network scanning from your 810.

---

### Post by blegs38552 on 2010-05-12
[QUOTE=prtsmgr;9284218]I have an Epson Artisan 810 as well.
I know it will not work with xsane.
You will need to downlaod and install *Image Scan! for Linux* from the links I provided in order to get network scanning from your 810.[/QUOTE

After much trial and error, got it to install and to scan.

This is the reason that I still say that Ubuntu is not for the faint of heart (with Win 7, it was a simple install from a CD and scan). Having said that, persistence is rewarded.

Thanks for your help.

---

### Post by mscout2004 on 2010-05-13
helped

---

### Post by prtsmgr on 2010-05-14
Here's something else that may help someone.

My power went out for about 1 hour tonight and after it came back on, I could not print.
What I found was that the Epson Artisan 810's IP Address had changed via DHCP.
I had to change printer properties to find the printer's new IP address.
I had to edit /etc/sane.d/epkowa.conf to reflect the new IP Address of the printer and everything was back to normal.

---

### Post by tjlytle on 2010-05-16
I have an Artisan 800, and assuming it's not that different from the 810, you should be able to use SANE, you just need to install newer backends. 

I had used this method on earlier versions of Ubuntu, and when I saw that 10.04 recognized the scanner I was pleasantly surprised. Until I tried to scan, had it pull a page halfway in, and give me an IO error. So much for that.

Just update sane-backend to a version => 1.0.21 as [outlined here]("http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html") via this [this SuperUser question]("http://superuser.com/questions/45835/epson-artisan-800-on-ubuntu-linux").

---

