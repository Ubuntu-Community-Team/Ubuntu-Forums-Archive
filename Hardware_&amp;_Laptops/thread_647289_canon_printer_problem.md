---
title: "canon printer problem"
date: 2007-12-22
forum: Hardware &amp; Laptops
---

### Post by zanzoon3 on 2007-12-22
hello, 

i'm hoping someone can help me with my canon i250 printing problem in clear, straighforward steps as i am a new ubuntu user and not really a computer savvy.

my canon i250 doesn't print PDF or post script files. when i print the file nothing happens, and when i point at the printer icon it appears as "Ready", but the state of the job is always "job stopped". if i try to print again i get: usr/lib/cups/filterpstocanonbj failed.

it prints out word files from open office. but what should i do to print all my PDF files?


thanks for the help, z

---

### Post by tgilber1 on 2007-12-22
Sounds like you're missing a postscript file.

CUPS - Common Unix Printing System is the default printing system used with Ubuntu.  Hence, when printing a pdf, CUPS does a few changes to the file before printing it

1.  Changes pdf to ps with pdftops script pdf - to - ps
2.  Changes ps with the ps command to get ready for raster pstops - ps - to - ps
3.  Finally, it converts it to a raster image file, ready for printing.  

You should have the following uncommented lines in your /etc/cups/cups.conf file

application/pdf         application/postscript  33      pdftops
application/postscript  application/vnd.cups-postscript 66      pstops
application/vnd.cups-postscript application/vnd.cups-raster     100     pstoraster

Note:  Lines may not be one right after the other or sequential

First of all make sure that you have the following files on your system

pdftops
pstops
pstoraster

You can check with the following command:  

"locate pdftops pstops pstoraster"

This previous command should display the following:

/etc/cups/pstoraster.convs
/usr/share/cups/mime/pstoraster.convs
/usr/lib/cups/filter/pstoraster
/usr/share/man/man1/pstops.1.gz
/usr/share/cups/mime/oopstops.types
/usr/share/cups/mime/oopstops.convs
/usr/bin/pstops
/usr/lib/cups/filter/pstops
/usr/lib/cups/filter/oopstops
/usr/share/man/man1/pdftops.1.gz
/usr/bin/pdftops
/usr/lib/cups/filter/pdftops

If these files do not exist, then install the following

"sudo apt-get install --reinstall cupsys cupsys-common xpdfutils psutils"

Recheck to verify files exist with the previously-mentioned locate command


Lastly, if this doesn't resolve your problem, please provide a copy of your /var/log/cups/*.log files.

You can upload the log files to the [http://www.pastebin.com](http://www.pastebin.com) and give the URL for accessing logs

---

### Post by L_V on 2008-01-26
Installing Canon i250 is really not a piece of cake.

Printing a simple pdf file seems to be a real nightmare.

zanzoon3: did you solve ? Feedback appreciated.

---

### Post by vadriaan on 2008-01-27
I printed nicely with kubuntu 6.10 to windows -.> epson R220
(the R220 was listed when I installed a new samba printer)

new laptop, fresh install of 7.10, no printing
tried new canon pixma i1800, no printing
(neither pixma i1800 nor R220 listed)

I tried " locate pdftops pstops pstoraster" and compared it with your output, minus the /etc/cups/pstoraser.*

then tried " sudo apt-get install --reinstall cupsys cupsys-common xpdfutils psutils"
give me the message "E: Couldn't find package xpdfutils"
Looked for it using Synaptic online.

any ideas?

---

### Post by L_V on 2008-01-27
The subject is "**canon** printer problem"
I did not know epson and canon is the same manufacturer.

> **vadriaan said:**
> give me the message "E: Couldn't find package xpdfutils"
It is not xpdfutils but xpdf-utils.

BTW, would appreciate to find somebody able to print a pdf file with a Canon i250.
Don't understand such complexity for pdf printing, on top of Canon i250 installation which is far to be obvious.

---

### Post by L_V on 2008-01-27
.

---

### Post by Jail on 2008-02-24
To print .pdf files with i250 in Gutsy I had to:
1. Install bjfilteri250_2.3-1_i386.deb as described in: [http://ubuntuforums.org/showthread.php?t=297775&highlight=i250]("http://ubuntuforums.org/showthread.php?t=297775&highlight=i250")
From the bjfiltercups-2.3-0.i386.rpm copy i250.ppd file to /usr/share/cups/model/
2.Get newer driver bjfilter-common-2.50-3.i386.rpm from: [http://download.canon.jp/pub/driver/bj/linux/bjfilter-common-2.50-3.i386.rpm]("http://download.canon.jp/pub/driver/bj/linux/bjfilter-common-2.50-3.i386.rpm")
3. Create .deb package from downloaded  .rpm:
**sudo alien --scripts bjfilter-common-2.50-3.i386.rpm**
4. Install  bjfilter-common-2.50-3.i386.deb
5. Add new printer using /usr/share/cups/model/i250.ppd file
PS. I am not sure if installing additional libs and creating symbolic links is still necessary.

---

