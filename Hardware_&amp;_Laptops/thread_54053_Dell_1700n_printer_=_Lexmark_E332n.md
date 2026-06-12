---
title: "Dell 1700n printer = Lexmark E332n"
date: 2005-08-03
forum: Hardware &amp; Laptops
---

### Post by Pan007 on 2005-08-03
After some gooling I found out that our schools Dell 1700n printers actually are Lexmark E332n printers with Dell cover.

Information about Lexmark driver for RedHat Linux and SuSe systems here:

[http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:452:0:0&emeaframe=&fileID=6084&searchLang=en](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:452:0:0&emeaframe=&fileID=6084&searchLang=en)

U can download the RedHat / SuSe driver here:

[http://www.downloaddelivery.com/srfilecache/print-drivers-linux-glibc2-x86.rpm.gz](http://www.downloaddelivery.com/srfilecache/print-drivers-linux-glibc2-x86.rpm.gz)

Hopefully I get the driver to work under Ubuntu Hoary.

Edit 1 hour later:

I did download the driver to my home directory, and unpacked it.
Then under terminal:

sudo alien -d print*.rpm
sudo dpkg -i print*.deb

When I try to add printer I still can't see it as an option under Lexmark.
Does anyone have tips to solve my problem.

---

