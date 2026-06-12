---
title: "Problems printing on an Epson SX200"
date: 2009-07-12
forum: Hardware
---

### Post by nanso on 2009-07-12
Hello,
I've been trying to get Ubuntu 8.10 to print on an Epson Stylus SX200 printer. I started by checking Epson's website, and from there got directed to [http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do) where I selected my printer and downloaded the deb packages for the printer driver and the scanner driver. The scanner driver installed OK with the package installer, because there was a package for Ubuntu 8.10 and later. That wasn't the case for the printer driver; I got an error for not having libltdl3, which as far as I understand, is not for 8.10. 
So, after some more searching I managed to install Gutenprint instead, I used 5.2.3-1lsb3.2_i386.deb. 
Now when I try to print anything, it says the job was sent to the printer, and it gets queued, appears to be printing and then disappears as if completed but the printer does nothing. The same happens when I try to print a test page from the Printer Properties of Ubuntu. 

Also, when I type lpstat -p in terminal I get 
printer Stylus-SX200 is idle.  enabled since Sun 12 Jul 2009 13:33:09 BST

Any idea what could be wrong?  

Thanks alot!

---

### Post by notoriousdbp on 2009-07-26
You should upgrade to 9.04.  I bought the same printer yesterday and hooked it up to my machine running xubuntu 9.04 and it installed and was able to print straight away without me having to do a thing.  When 8.10 was released the SX200 wasn't supported then but is now in 9.04

---

