---
title: "Epson L200 printer is printing an extra page"
date: 2012-11-17
forum: Hardware
---

### Post by rudregues on 2012-11-17
Every time I order the printer to print something, it prints an extra page that seems like a printer status page or a test page, I don't know how to define this page. The contents of this extra page are posted below:

Media Limits: 0.12 x 0.12 to 8.15 x 11.58
Job ID: EPSON-L200-213
Driver: EPSON.PPD
Driver Version:
Descripion: EPSON L200
Driver Version: EPSON L200
Make and Model: Epson Stylus N10 N11 Series - epson-inkjet-p
Printer: EPSON-L200
Created at: Thu Nov 15 19:09:10 2012
Printed at: Thu Nov 15 19:09:10 2012

I've tried to reinstall the drivers too, but it don't worked.... 

  [ ]'s

---

### Post by pdc on 2012-11-17
it wasn't clear to me whether you are using the epson drivers

[http://ubuntuforums.org/showthread.php?t=1671378](http://ubuntuforums.org/showthread.php?t=1671378)

post #1 in the above thread describes how to download the drivers Epson makes available:

the printer driver comes from Epson's older repository store: Avasys;

I can find a scanner driver on Epson's newer site: [http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)

but no printer driver there.........so suggest using the avasys link;

you could then see if this alternative driver works better for you

---

### Post by rudregues on 2012-11-17
Thanks for reply pdc, but the thread you mention is the one I've used before to install my printer drivers. And the same thread was used to reinstall the drivers in order to solve the strange behavior of the printer and failed.

   [ ]'s

---

### Post by rudregues on 2012-12-01
_Update_:

I've found two issues like mine, but with HP printers.

[http://askubuntu.com/questions/194225/disable-printing-extraneous-job-info-when-i-print-a-images](http://askubuntu.com/questions/194225/disable-printing-extraneous-job-info-when-i-print-a-images)
[https://answers.launchpad.net/hplip/+question/207642](https://answers.launchpad.net/hplip/+question/207642)

I don't think is a driver bug/problem, epson driver and hp driver are different. Maybe  a CUPS bug or an error related to Ubuntu...

---

### Post by revmarkp on 2012-12-12
I'm having the same issue. On both an HPC6380 inkjet and an HP2100n laserjet. I don't think it's a printer issue, rather an HPLIP or cups issue.

Can anyone see what's happened? I suspect an 'option' has got turned on by default in a newer version of the hplips or cups. only happens with PDF printing for me.

---

### Post by rudregues on 2012-12-16
> **revmarkp said:**
> I'm having the same issue. On both an HPC6380 inkjet and an HP2100n laserjet. I don't think it's a printer issue, rather an HPLIP or cups issue.

Can anyone see what's happened? I suspect an 'option' has got turned on by default in a newer version of the hplips or cups. only happens with PDF printing for me.

Are you using 12.04?
I really looked for such an option like that, everywhere, but failed... :-(
Why not cups? It's a program related between hplip and epson driver.

 [ ]'s

---

### Post by revmarkp on 2012-12-17
I'm on 32bit 12.04

> 
Why not cups? It's a program related between hplip and epson driver.


you're right in suggesting this being a cups, not hplip issue, as the problem is experienced beyond hplip...

---

### Post by rudregues on 2013-01-02
I've tested the printer on my Xubuntu 12.04 32 bits without any problems. Later, I'll update Xubuntu and test again.

  [ ]'s

---

### Post by rudregues on 2013-02-17
_Update:_

I've installed Ubuntu 12.10 64 bits, installed n10&n11 stylus driver and there is no problem. But an interesting thing:
go to printers-> double click epson l200->configuration and click "print test page"
this page is the same "extra page" I have in Ubuntu 12.04, unique  difference is the "test page" has some images showing the different  colours like magenta, black, blue, green etc just like this [http://www.danmaher.com/images/printer1.jpg](http://www.danmaher.com/images/printer1.jpg)
 So, the bug is not an "extra page" but an extra "printer test page" without images.

The bug in launchpad: [https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1085559?comments=all](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1085559?comments=all)


 [ ]'s

---

