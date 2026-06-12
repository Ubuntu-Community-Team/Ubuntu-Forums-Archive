---
title: "Xerox Workcentre 5020 doesn't work in Ubuntu"
date: 2010-02-27
forum: Hardware
---

### Post by Almat on 2010-02-27
Hello there,

Before posting a thread here i have googled a lot to find a solution to make Xerox Workcentre 5020 work under ubuntu 9.10 but unfortunately i could not find anything to make that printer work without using windows in vbox at work. Though xerox claims that workcentre 5020 works under linux, they only provide driver for network version of that printer and not for ordinary version. 
with regard to that i would like to ask does anybody have any idea or know how to solve this issue?

---

### Post by vikdak on 2010-11-24
I had the same problem, but while going through some website, which I unfortunately can't find anymore, I have the following solution.

1. Go through the usual process of installing the printer.
2. When it asks for drivers, instead of choosing any brand, choose generic.
3. Next enter PCL 5, and just click through. 
4. You are set. 

I must mention that I have lucid.

---

### Post by cl17g on 2012-11-21
> **Almat said:**
> Hello there,
 
Before posting a thread here i have googled a lot to find a solution to make Xerox Workcentre 5020 work under ubuntu 9.10 but unfortunately i could not find anything to make that printer work without using windows in vbox at work. Though xerox claims that workcentre 5020 works under linux, they only provide driver for network version of that printer and not for ordinary version. 
with regard to that i would like to ask does anybody have any idea or know how to solve this issue?


Apparently Xerox provides a driver for the network version of this printer, only for 32 bit machines. I tried to install it in my 64 bit PC, but of course installation failed. 



Has anyone succeeded in installing the Xerox WorkCentre 5020 dn driver on a 64 bit machine?


Btw, I am using Ubuntu 12.04 (precise) 64-bit, Kernel Linux 3.2.0-33-generic.


Thank you!

---

### Post by kurt18947 on 2012-11-21
> **cl17g said:**
> Apparently Xerox provides a driver for the network version of this printer, only for 32 bit machines. I tried to install it in my 64 bit PC, but of course installation failed. 



Has anyone succeeded in installing the Xerox WorkCentre 5020 dn driver on a 64 bit machine?


Btw, I am using Ubuntu 12.04 (precise) 64-bit, Kernel Linux 3.2.0-33-generic.


Thank you!

I don't have that machine or any Xerox product for that matter.  Brother does the same thing though, only providing 32 bit drivers.  Here is the line Brother uses to install 32 bit .deb packages on a 64 bit machine:

Command (for dpkg)  :  dpkg  -i  --force-all  (drivername.deb)

Maybe try the same thing with the Xerox package and see if you get a complaint?  I don't know if it'd work or not but don't think there'd be any harm.

---

### Post by cl17g on 2012-11-26
I've been out of office a few days, so I couldn't try before. I followed your advice and it worked smoothly! Thank you.

---

### Post by cl17g on 2012-11-27
Unfortunately I have to partially correct my previous post. Installation was successful and the printer works fine. However I have now a problem with apt-get.  If I run apt-get upgrade I obtain
 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 xrworkcentre5020dn:i386 : Depends: libcupsys2:i386 (>= 1.2.7)
E: Unmet dependencies. Try using -f.
 
But if I use -f I get
 
The following packages will be REMOVED:
xrworkcentre5020dn:i386
 
which is the printer driver package!
Any idea?

---

### Post by cl17g on 2013-03-28
[FONT=arial]After a few months I decided to face the problem of the Xerox Workcentre 5020 dn driver again.

Since the main problem is that the driver depends on libcupsys2, which has been substituted by libcups2, I thought that a possible solution could be that of substituting any reference to libcupsys2 in the driver with libcup2. Therefore I unpacked the .deb file (using the package manager) and edited the /DEBIAN/control file by substituting libcupsys2 with libcups2. Finally I re-packed the .deb file using [/FONT]

fakeroot dpkg-deb -b mydirectory
[FONT=arial]
I reinstalled the driver (using the option --force-all, since I intended to install it on a 64 bit machine) and the printer (using CUPS). 

Well.... IT WORKS!!!

I hope that this be useful to others.

Best regards to all of you.


  [/FONT]

---

### Post by frol_and on 2013-11-16
I have the problem of the Xerox Workcentre 5020 b driver. I did everything you said, but the problem remains =(

---

### Post by efflandt on 2013-11-16
Most business class printers understand either postscript or HP PCL printer language (someone above said PCL 5 worked). Many years ago when I needed to print a PDF booklet from my Linux laptop at a Kinkos Copy Center (before they were FedEx Office) and before cups, using a printcap file, there was no Linux driver for the Xerox printer, so I simply set it as generic level 2 postscript and that worked. I forget if it was networked or parallel port. But if this printer is connected by USB, I have never used one of those (I stick to network printers).

---

