---
title: "Canon i250 in Breezy? Help!"
date: 2005-10-22
forum: Hardware &amp; Laptops
---

### Post by johnkennethhughes on 2005-10-22
I am having trouble with my Canon i250 USB printer in Breezy (GNOME version). I have downloaded and installed the drivers from [http://www.canon.com.au/products/printers/colour_bj_printers/i250_drivers.html](http://www.canon.com.au/products/printers/colour_bj_printers/i250_drivers.html) (using the 'alien' tool to convert the rpm packages into deb packages). When I try to add a new printer, the printer is detected correctly and it selects the new driver automatically. However, when I try to print a test page, or anything else, nothing happens.

Any ideas?

---

### Post by Breezy Badger on 2005-10-27
I also need to know how to get this damn printer working, same exact one.

Anyone?

---

### Post by kamosbg on 2005-11-11
Pls help me with canon i250+ubuntu breezy badger

---

### Post by nder on 2005-12-14
Has anyone else had this problem?  Is there a solution.  I am currently downloading the drivers, but dont have the printer to test them now.  Anything I should know?

---

### Post by nder on 2005-12-14
I installed the drivers using alien after my attempted compilations failed.  The printer is detected, but pages do not print :(

---

### Post by nder on 2005-12-17
Has no one had success in getting the i250 to work in Breezy?  I'd hate to tell my friend that the superior OS I just installed on his computer is unable to print unless he buys a $37 driver!

---

### Post by Simon741 on 2006-03-31
There is a great description of how to install the i250 on Ubuntu at [http://wiki.ubuntuusers.de/Canon_i250]("http://wiki.ubuntuusers.de/Canon_i250") in German

As contribution to the ubuntu-community, I try to translate it here. Maybe some native English speaking person can check the grammar and orthographe. 

*********************************************************************

The Canon i250 is one of the cheapest models of Canon, if not the cheapest one. Unluckily the printer is not directly supported by a OpenSource project. However Canon offers a [driver for Linux at it's webpage]("canon.co.nz/products/printers/colour_bj_printers/i250_drivers.html") that can be made to work with some additional hacks . 

The method described here  makes use of the available RPMs and has to be considered as somewhat unclean, but it works. 

**Download the files**

From the above mentioned webpage of Canon, download the two files [bjfiltercups-2.3-0.i386.rpm]("http://www.canon.co.nz/drivers/confirm.aspx?f=http%3a%2f%2fdownload.canon.com.au%2fbj%2fi250linux%2fbjfiltercups-2.3-0.i386.rpm") and [bjfilteri250-2.3-0.i386.rpm]("http://www.canon.co.nz/drivers/confirm.aspx?f=http%3a%2f%2fdownload.canon.com.au%2fbj%2fi250linux%2fbjfilteri250-2.3-0.i386.rpm").

**Convert the RPM-packages into Debian packages**

The donwloaded RPM-files have to be converted into Debian-packages with the help of the command line tool alian (eventually you have to install this via Synaptic):
[INDENT]:~$ alien bjfiltercups-2.3-0.i386.rpm bjfilteri250-2.3-0.i386.rpm[/INDENT]

**Install additional packages**

After activating Universe, you have to install the following packages:
[LIST]
[*]libxml1
[*]libglade0
[*]libpng2
[*]libtiff4 (ehemals libtiff3g, weitere Infos s.u.)
[/LIST]

[INDENT]:~$ sudo apt-get install libxml1 libglade0 libpng2 libtiff4[/INDENT]

Eventually other dependancies are missing.

**Installing the packages**
Pakete installieren

The converted Debian-packages can now be installed:
[INDENT]:~$ sudo dpkg -i bj*.deb[/INDENT]

Now the driver is installed, but there are some symbolic links to libraries missing that are not set correctly through the installation:
[INDENT]:~$ sudo ln -s /usr/lib/libcnbpcmcm180.so.6.03.1 /usr/lib/libcnbpcmcm180.so
:~$ sudo ln -s /usr/lib/libcnbpess180.so.1.4.0 /usr/lib/libcnbpess180.so
:~$ sudo ln -s /usr/lib/libcnbpcnclui180.so.3.0.0 /usr/lib/libcnbpcnclui180.so
:~$ sudo ln -s /usr/lib/libcnbpcnclbjcmd180.so.3.0.0/usr/lib/libcnbpcnclbjcmd180.so
:~$ sudo ln -s /usr/lib/libcnbpcnclapi180.so.3.0.0 /usr/lib/libcnbpcnclapi180.so[/INDENT]

These libraries belong to the driver and the driver, respectively the binarly bjfilteri250 are not linked to these files.

Because the driver depends on the packe libtiff3g, which is not maintained anymore for Breezy, an additional link has to be set:
[INDENT]:~$ sudo ln -s /usr/lib/libtiff.so.4.1.3 /usr/lib/libtiff.so.3[/INDENT]

If everything went well, you should now be able to launch bjfilteri250 in the console. If everything is ok, you should get the following text or something similar:

[INDENT]BJLSTART
ControlMode=Common
SetTime=20050413235027
BJLEND[/INDENT]

To stop the test, simply hit "Ctrl" + "C".

**Activating the printer**

Finally the printer can be activated in Genome under "System" -> "Administration" -> "Printing" or under KDE: (has to be completed)

---

### Post by johnkennethhughes on 2006-04-22
That works perfectly! Thank you!

---

### Post by Breezy Badger on 2006-06-27
Ok so this never did work for me in Breezy.  Does anyone know if it is the same for Dapper, or should we start a new thread?

---

