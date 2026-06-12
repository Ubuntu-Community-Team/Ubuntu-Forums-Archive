---
title: "Epson EPL-6200L doen't work"
date: 2005-06-21
forum: Hardware &amp; Laptops
---

### Post by linuxaway on 2005-06-21
Dear all
My printer, Epson EPL-6200L, doesn't not work at all. Ubuntu did not detect my printer and I select manually the driver. But when I press on 'Print a test pages', my  printer doesn't run. Could you tell me how to do now?
Thanks for your support

---

### Post by Zelut on 2005-06-21
check out this page at linuxprinting.org... (great place to check out for printing under linux)

[http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-EPL-6200L](http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-EPL-6200L)

this is info & specs/drivers for your model.  I hope this helps

---

### Post by linuxaway on 2005-06-21
Dear Mr. kuyaedz and all
I have checked the page 
[http://www.linuxprinting.org/show_p...Epson-EPL-6200L](http://www.linuxprinting.org/show_p...Epson-EPL-6200L)
and seen some notes below.
I learn that my printer is difficul to work in linux except mandrake 10.2 . But I hope you could help me more. 
Thanks for your support.

.......................................................................................................................
User Notes

The epsonepl driver has been fixed, it now works for the 6200L model.

# txapelgorri edited:
# The driver works fine (EPL 6200L), but you need 2 things to make it work (at least in my case: Debian):

First you need to install gs-afpl (Sourceforge or apt-get non-free :( ).
Secondly you need to modify '/usr/lib/cups/filter/pstoraster' script that is used by cups yo call gs. Below you'll find a line calling gs-eps binary. Change it and put gs-afpl instead.

Enjoy!

The printer doesn't work in my case. I use Debian, downloaded the PPD file and configured
cups, but it reject all works. I configured a pstoraster too but the problem still on.
Someone made work a printer..???

---------------------------------------------------------------------------------

--MANDRAKE USERS--

19/05/2005
Today i installed Mandrake 10.2 (2005LE) and my EPL-6200L started working perfectly with the driver embedded in the OS.
With 10.1 (rpm driver, ppd or anything else) didn't work at all and i never could fix the problem.
I strongly reccomend an upgrade to 10.2.
Luca (Italy)
............................................................................................................

---

### Post by eminux on 2005-10-01
me too, I have an eplson epl-6200l and it doesn't work at all. I read more and more but I can't resolv the problem...
any news?

---

### Post by eradan on 2007-11-17
After the dist-upgrade to Gutsy my Epson EPL 6200L doesn't work anymore.

I've found a trick to print but it's not a good solution:

The printer works if I force the installation of this packages:

* gs-afpl_8.53-1_i386.deb
* libjasper-1.701-1

you can download them here:
* [http://packages.ubuntu.com/feisty/libs/libjasper-1.701-1](http://packages.ubuntu.com/feisty/libs/libjasper-1.701-1)
* [http://packages.ubuntu.com/feisty/text/gs-afpl](http://packages.ubuntu.com/feisty/text/gs-afpl)

and install it using:

* sudo dpkg -i libjasper-1.701-1_1.701.0-2ubuntu0.7.04_i386.deb
* sudo dpkg -i --force-conflicts gs-afpl_8.53-1_i386.deb

Now you can proceed to install the printer using this ppd file:

* [http://grappalug.homelinux.net/sections/03_Documenti/Epson_EPL6200L_su_Ubuntu/EPL-6200L.ppd.txt](http://grappalug.homelinux.net/sections/03_Documenti/Epson_EPL6200L_su_Ubuntu/EPL-6200L.ppd.txt)

(note that this is a modified ppd that use the gs-aflp as interpreter)

and the debian package driver:

* [http://grappalug.homelinux.net/index.php?mod=none_Fdplus&fdaction=download&url=sections/03_Documenti/Epson_EPL6200L_su_Ubuntu/epsoneplijs_0.4.0-2_i386.deb](http://grappalug.homelinux.net/index.php?mod=none_Fdplus&fdaction=download&url=sections/03_Documenti/Epson_EPL6200L_su_Ubuntu/epsoneplijs_0.4.0-2_i386.deb)

Now the printer should work (at least: it does on my system).

But *unfortunaly* you cannot upgrade your system anymore!!!
Anytime you'll try to dist-upgrade you'are going to have back an error message due the presence of the gs-afpl package!

You can remove it, upgrade your system and reinstall gs-afpl again...

Yes, this is just a placebo!
I hope that someone could give us better informations for Gutsy!!!

A better and suitable solution should be to find a proper filter (in place of gs-afpl) to use in the ppd file that produce the postscript to send to the printer...

Any ideas?

Cheers,
Ivan

---

### Post by marlus on 2008-05-11
Check out my solution on Hardy here:
[http://ubuntuforums.org/showthread.php?t=696363&highlight=6200l](http://ubuntuforums.org/showthread.php?t=696363&highlight=6200l)

---

