---
title: "lpr or enscript for ubuntu"
date: 2004-11-26
forum: Hardware &amp; Laptops
---

### Post by spb on 2004-11-26
Hi,

I'd like to be able to print by dumping a text file to my printer via a command 

lpr -Pprintername filename

but I'm finding that when I do this it prints as if it were a dotmatrix page.  

Is there a way to fix this from within the default installation?

At my work I've been using enscript to control my printing (2-up with prettyprint -- very nice...).  Enscript doesn't seem to be included in the ubuntu repository.  Is adding the debian repositories and installing enscript the best method to solve the problem?

Thank you,
spb

---

### Post by Magneto on 2004-11-26
try cupsys-bsd    it has lp commands you can use that print via cups

---

### Post by WW on 2004-11-27
**enscript** is available in Ubuntu's **universe** component of their repository.

---

### Post by spb on 2004-11-27
[QUOTE=Magneto]try cupsys-bsd    it has lp commands you can use that print via cups[/QUOTE]

I think that cupsys-bsd is installed already and is the lpr command that is being used.  

Everything seems to work just fine when I'm printing from a program such as emacs or openoffice.  The problem is when I try to use lpr to dump text to the printer.

---

### Post by Magneto on 2004-11-27
[QUOTE=spb]I think that cupsys-bsd is installed already and is the lpr command that is being used.  

Everything seems to work just fine when I'm printing from a program such as emacs or openoffice.  The problem is when I try to use lpr to dump text to the printer.[/QUOTE]
 are you sure it isnt the real lpr? by default the real lpr is installed
i thought the cupsys-bsd version actually had the lpr-cups commands which is used just like lpr cept it uses the cups backend

---

### Post by spb on 2004-11-28
It looks like cupsys-bsd is there:

scott@jameson:~ $ dpkg -l | grep 'cupsys-bsd'
ii  cupsys-bsd     1.1.20final+cv Common UNIX Printing System(tm) - BSD comman
scott@jameson:~ $

but I don't see a file "lpr-cups"  

scott@jameson:~ $ sudo find / -name 'lpr-cups' -print
Password:
scott@jameson:~ $

I'm using Ubuntu Linux 4.10 maybe earlier distributions didn't install cupsys-bsd?  

So with the cups version of lpr how do I get the margins correct?  Is there a flag that I have to set?  I don't see anything in the man page for lpr or lp that suggests I can force margins.  

I should mention also that when I print the test page it appears that the borders run off of the edge of the paper -- I assumed that this means that the test page is defaulted to A4 since I seem to be able to print to Letter from Emacs, xpdf, Openoffice, and my windows XP machine (via smb).  

spb

---

### Post by Magneto on 2004-11-28
Im using Hoary I have cupsys-bsd too- just checking

> So with the cups version of lpr how do I get the margins correct? Is there a flag that I have to set? I don't see anything in the man page for lpr or lp that suggests I can force margins.

I should mention also that when I print the test page it appears that the borders run off of the edge of the paper -- I assumed that this means that the test page is defaulted to A4 since I seem to be able to print to Letter from Emacs, xpdf, Openoffice, and my windows XP machine (via smb).


you can set the paper type - letter,A4 etc by opening the gnome printer config app - Computer----->System Configuration------> Printing  right click your printer and choose properties and change the paper type

If you really need to adjust the actual margins there is a ppd file which contains the actual margin information that you must change- /etc/cups/ppd/*.ppd  which is the ppd file for your printer  
check out [http://www.linuxprinting.org/](http://www.linuxprinting.org/) for information regarding changing that file
[http://www.cups.org/faq.php?25](http://www.cups.org/faq.php?25)   forcing margins

The lp and lpr you are using all use the cups configurations and invoke cups

---

### Post by spb on 2004-11-28
[QUOTE=Magneto]
you can set the paper type - letter,A4 etc by opening the gnome printer config app - Computer----->System Configuration------> Printing  right click your printer and choose properties and change the paper type[/QUOTE]

I've done this and is works except for when I use lpr.  This is what surprises me.  Within applications it prints to the Letter size that I specified in CUPS configuration, but if I dump a file to the printer with lpr it doesn't.  

[QUOTE=Magneto] The lp and lpr you are using all use the cups configurations and invoke cups. [/QUOTE]

I thought so too, but I don't know that they are since they don't seem to behave as they should.

---

### Post by spb on 2004-11-28
I just connected my Espon Dotmatrix "LX-300" printer to the machine.  When I print to this with lpr I get the same problem.  Left two characters of each line are cut-off, but I can print just fine to the dot-matrix printer with openoffice.

---

