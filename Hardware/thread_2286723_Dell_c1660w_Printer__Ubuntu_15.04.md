---
title: "Dell c1660w Printer | Ubuntu 15.04"
date: 2015-07-14
forum: Hardware
---

### Post by ghostlove2 on 2015-07-14
Hi all. I've just switched back to Ubuntu from Windows and find myself without a working printer - my Dell c1660w just will not work with this operating system.

I have found [this driver]("http://cybercom.net/~dcoffin/hbpl/"), however I don't know what I'm doing wrong, but it simply isn't doing anything. My computer recognises my printer, but when I go to actually print something it just does nothing and the printer gives me an error message.

Can anyone help? I don't want to switch back to Windows and I don't want to have to buy a new printer. :/

---

### Post by CitadelUniversal on 2015-07-14
Hello, I've found this in my searches for the printer - do these instructions help [http://printersquestions.com/How-to-install-Dell-C1660w-on-Ubuntu.html](http://printersquestions.com/How-to-install-Dell-C1660w-on-Ubuntu.html)

---

### Post by ghostlove2 on 2015-07-14
I'm afraid not, CitadelUniversal - that's just the basic installation instructions for a generic printer, and Ubuntu doesn't have the drivers for this one as standard.

---

### Post by nicholson-mark on 2016-04-07
I have had much the same issue.   I finally tracked down the sources for the driver ([http://cybercom.net/~dcoffin/hbpl/](http://cybercom.net/~dcoffin/hbpl/)), the original code ([http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/)).   I debugged it and got it to work on 14.04.  There were some issues in the interface to CUPS and a script was not behaving correctly.   I spent the time to update the packaging so there is now a PPA which contains the .debs for i386 and amd64.  This is my PPA:

ppa:nicholson-mark/ppa

You'll grab 3 packages:

printer-driver-foo2zjs-common
printer-driver-foo2zjs
printer-driver-foo2zjs-hbpl1

This provides an update to the latest source baseline, as well as the changes to support HBPLv1 printers.

---

### Post by speddingjr on 2017-01-11
Hi Mark, I did try the ppa route but despite going through the steps I couldn't get it to work for me.

Luckily the Xerox Phaser 6000B driver did work on my 64bit AMD laptop running lubuntu 16.10.

I had to download the xerox zip file and deal with the two dependencies (that it didn't mention at all) but it did work and now the c1660w works nicely.

I was going to message you for some advice but luckily I found a workaround.

Thanks for your help.

---

