---
title: "xerox printer PE16 driver?"
date: 2008-11-13
forum: Hardware
---

### Post by edilsonka on 2008-11-13
Dear all, good day for you; 

Pls can someone inform where can I find the XEROX PE16 driver for linux? Or equivalent driver? 

I've already searched on Google for such driver, and I do not have other idea where to find it out ...

Tks in advance, 

B. Regards;

Edilson

---

### Post by igor4u on 2008-12-04
Lexmark X215, Samsung SCX-4216F and Xerox PE 16 appears to be the same printer. Download the SCX-4216F drivers from samsung site and run installation program. This will install a configuration program and make the driver available in the CUPS printer setup. Printing works fine over smb and socks, haven't tested scanning.

See page [http://www.samsung.com/us/support/download/supportDown.do?model_nm=SCX-4216F&mType=DR&vType=L&disp_nm=SCX-4216F](http://www.samsung.com/us/support/download/supportDown.do?model_nm=SCX-4216F&mType=DR&vType=L&disp_nm=SCX-4216F)
Download driver from [http://org.downloadcenter.samsung.com/downloadfile/ContentsFile.aspx?CDSite=us&CttFileID=247799&CDCttType=DR&ModelType=N&ModelName=SCX-4216F&language=&cate_type=all&VPath=DR/200707/20070725085320093_UnifiedLinuxDriver.tar.gz](http://org.downloadcenter.samsung.com/downloadfile/ContentsFile.aspx?CDSite=us&CttFileID=247799&CDCttType=DR&ModelType=N&ModelName=SCX-4216F&language=&cate_type=all&VPath=DR/200707/20070725085320093_UnifiedLinuxDriver.tar.gz)
1. Download and extract the driver
2. Open ''Root Terminal''
3. Execute installation program.
$ sudo cdroot/autorun
4. Choose driver from a list and install

---

### Post by Eupator on 2010-07-03
I used built-in driver of Samsung SCX 4200
And it's works!  :D
[http://nocoffee.ru/blogs/24/53/](http://nocoffee.ru/blogs/24/53/)

---

### Post by taglitis on 2010-11-27
Hello igor4u and Eupator I also have a problem with installtion of Xerox PE 16 to Ubuntu. I found your links but they are broken. Could you please renew the links or email me drivers. 

Thank you in advance!

---

### Post by ncelyg on 2013-01-29
have problems with my MFP to scan under ubuntu 13.04
the printer driver from the xerox PE16 works perfectly, but I can not use the scanner, I'm using the MFP xerox PE16 by usb. can someone help me with the problem of the scanner with xsane.

---

