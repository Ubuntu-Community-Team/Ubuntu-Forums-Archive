---
title: "Driver for Epson CX5900"
date: 2007-09-24
forum: Hardware &amp; Laptops
---

### Post by DragonionS on 2007-09-24
I have Ubuntu 7.04 installed on my notebook. Some weeks ago I bought Epson CX5900 but there were drivers for only Windows and Mac OS X. I've tried to find the necessary driver at the Administration/Printer. I have found there drivers for CX5800, CX6000 among them but noone for CX5900. What have I to do? Is there some way to solve this problem?

---

### Post by gautada on 2007-09-24
The [Open Printing Database]("http://openprinting.org") reports that the [CX5900]("http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_CX5900") is only partially supported.  You are pretty much on your own, sorry.  Try to find a proprietary driver from Epson.

---

### Post by DragonionS on 2007-09-24
[COLOR="DarkRed"]**I've changed this instructions becouse of some mistakes.**[/COLOR] This instruction works well with my Asus A7J notebook and Epson STYLUS CX 5900.

The letter that was sent by me to the Epson support has given an answer.

So, for those, who have the newest Epson printers/scanners this information could be useful.

First of all visit this link and choose your type of printer:
[http://www.avasys.jp/english/linux_e/dl_spc.html]("http://www.avasys.jp/english/linux_e/dl_spc.html")

Then after choosing your type of printer you will see the page with the list of available packages. There two variants of these packages: rpm and source (tar). And we have to choose source of cource :) 

Following the instructions you will install this drivers.

**[COLOR="DarkRed"]Method 1. Installation using tar.gz2 archives[/COLOR]**
1. You have to install cups using apt-get (aptitude). It is ok if you install some another packages related to cups etc.
2. Then open your archive with pipslite and copy the directory with files out of archive.
3. In console enter this directory.
4. Now we have to do some coomon things for it:
> ./configure
make
make install
**ATTENTION!!!** If there will be some errors during compilation you have to read the message about the reason. The most of errors could be if there is no some package being installed on your system.

The we have to move to the /usr/share/pipslite directory to continue installation.
If you've not found it use whereis command in console. (**whereis pipslite**).

Now we have to execute 
> /usr/share/pipslite/scripts/setup-cups.sh
Nextly there will be some questions and as the result there will be pipslite being installed on your system but this is not the end. ;)
The next step: 
**pipslite-install**
You have to be gtk+1.2 installed on your system for it and you have your **printer to be enabled**

Now we have to:
> lpadmin -p printer_name -E -v ekplp:/var/run/ekplp0 -m ppd_file
printer_name - your choice how to name your printer and ppd_file have to be in the cups/models. You have to find it too.
**ATTENTION!!!** You could have cups in (K)Ubuntu another directory than pipslite is looking for. In this case you have to find this directory using (**whereis cups**) and copy it content to the real cups directory.

Now restart your cups you are welcome to print using CX 5900 :)

**[COLOR="DarkRed"]Method 2. Installation using rpm package.[/COLOR]**
1. You have to install cups and rpm using apt-get (aptitude). It is ok if you install some another packages related to cups etc.
2. Install rpm package:
> rpm -Uvh --nodeps pipslite-1*.rpm
3. Execute using console:
> /usr/share/pipslite/scripts/setup-cups.sh
4. Run pipslite-install through the console. As was written above you have to be gtk+1.2 installed on your system for it and you have your **printer to be enabled**
5. Now we have to:
> lpadmin -p printer_name -E -v ekplp:/var/run/ekplp0 -m ppd_file
printer_name - your choice how to name your printer and ppd_file have to be in the cups/models. You have to find it too.
**ATTENTION!!!** You could have cups in (K)Ubuntu another directory than pipslite is looking for. In this case you have to find this directory using (**whereis cups**) and copy it content to the real cups directory.

Now restart cups and your CX 5900 is ready to print.

I suppose it helps someone.

---

### Post by NZ-Wanderer on 2007-11-15
I'm using Gutsy, and alas your instructions didn't work...

I managed to get a RPM and a TAR.GZ file (cause there was no "source" that you mentioned.above.
I extracted the TAR and tried the sudo autocong -f you mentioned but got a "command not found" error

and that's as far as I got...

Any ideas please??

---

### Post by DragonionS on 2008-05-11
I've changed this mini HOWTO. :) I hope it is better and more usable.

---

