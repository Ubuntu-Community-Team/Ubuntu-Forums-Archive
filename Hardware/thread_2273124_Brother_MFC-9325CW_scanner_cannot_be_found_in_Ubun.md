---
title: "Brother MFC-9325CW scanner cannot be found in Ubuntu 14.04"
date: 2015-04-10
forum: Hardware
---

### Post by knight69 on 2015-04-10
My Brother MFC-9325CW printer, scanner and fax were all working wonderfully under Ubuntu 12.04.  When I upgraded to Ubuntu 14.04 (Trusty (which seems to be not so trustworthy)) on my desktop (intel i5) computer, my printer failed, my scanner failed and my fax failed.  I downloaded and installed the Brother driver install tool from the Brother site that reported successfully installed all the drivers for the printer, scanner and fax.  The printer now works beautifully, but the fax cannot be found.  (I have not tried the fax, yet.)  The scanner works perfectly under windows which is installed as a virtual guest on my computer.  

Instructions for correcting this problem appear to be for Precise Pangolin and not for Trusty.  

Results from the command [FONT=courier new]sane-find-scanner[/FONT] report that there is no usb scanner.  Results from the command [FONT=courier new]lsusb[/FONT] report that there is.  I can find no tools for managing, installing or configuring scanners.  

HELP ME! :mad:

---

### Post by knight69 on 2015-04-11
More info.  xsane simple scan reports "Failed to open device 'brother 4; bus 2; dev 1; invalid argument"
                no such device reported at that location by lsusb
                lsusb -v reports "Couldn't open device, some information will be missing" for the Brother printer/scanner
                Downloaded and installed drivers from Brother a second time, still no scanner.
In /etc/sane.d folder, there is no configuration file for brother scanners.

---

### Post by gannet2 on 2015-07-07
Sorry, I can't help but I think I can add a little further confusion.  I have a PC running 14.04 communicating with with a brother MFC-J5910DW over a wireless LAN.  All, until recently, was working fine.  The printing bit is still OK but the PC can no longer see the scanner.  I tried the usual things like making my account a member of the scanners group, deleting the contents of my ~/.sane directory, uninstalling and re-installing the drivers.  Xsane still gives me "No devices available" but I no longer get the "Failed to open device 'brother ..." message.

The interesting part is that, before the problem appeared, I cloned my hard disk so that I could upgrade my laptop from XP to Linux.  It worked straight away and I only had to make a few changes to allow it to work without a permanent connection to the office server.  (As an XP refugee it amazed me that I could do this although it probably shouldn't have done.)  The point is that the laptop can still see the MFC-J5910DW printer/scanner and I can scan documents in the same way as I used to on the desktop.  Both laptop and desktop run virtually the same packages and both are kept up to date with the mintUpdate manager.

**If anyone can suggest where I should be looking**, I could compare the files on the two computers and perhaps find the source of the problem.

---

### Post by saou on 2015-08-30
In case anyone is still having problems with using Brother scanner in 14.04, here's a post that helps  me solve the problem (at least for MFD7420):  [http://metricrat.co.uk/brother-dcp-540cn-scanner-on-xubuntu-14-04/](http://metricrat.co.uk/brother-dcp-540cn-scanner-on-xubuntu-14-04/)

Key:
1) install all drivers from brother websites
2) copy everything from **/usr/lib64/sane** to **/usr/lib/sane**
3) copy everything (not folders just files) from **/usr/lib64** to **/usr/lib**

 4) overwrite anything that is there already.

 5) Reboot

Thanks to the author of this post for sharing his information!  YMMV.

---

