---
title: "Brother MFC-7820N help!!!"
date: 2006-07-27
forum: Hardware &amp; Laptops
---

### Post by pointym5 on 2006-07-27
I've got a new Brother MFC-7820N that I'd like to get working as an Ethernet-resident printer for a network of Ubuntu machines.  I came to believe that it would be easy to get it working, but so far it has not been easy at all. Nothing from the Brother website or from any other source has made the printer do anything at all.

The printer is correctly on the network. All machines involved can ping it successfully.

I've tried the Gnome CUPS manager and it hasn't worked in any of the various permutations I've tried. (As far as I can tell, attempting to use it to set up an LPD remote host flat-out doesn't work; the tool will not save such a configuration.)

Am I the only person in the world trying to do this?
:confused:

---

### Post by pointym5 on 2006-07-27
:p Here's what I did to get it to work via CUPS:
[list=1][*]First, I enabled the CUPS web UI - not because I like it, but because gnome-cups-manager generally segfaults for me all the time.  I don't know why and I don't care.[*]The printer has an HTTP-accessible interface.  You have to log into it; the factory username/password is "admin"/"access".[*]From the printer's web UI, I navigated to "Network Configuration", and then to the "Console" link.  That provides a weird "command line" interface.  That made me log in again, though subsquently it hasn't.  Anyway once there I was able to find the "SH IPP" command, which dumped out the precious info I'd been looking for: the IPP URIs to use. I picked one that looked like "http://my.printer.name:631/ipp".[*]I set up the printer in CUPS as an Internet Printer "http" and used that address.  For the driver I picked (randomly) the Brother HL-7050N driver (Foomatic/PostScript).[*]Clicked "Print Test Page" and it worked. Printing from Firefox also worked.[/list]

---

### Post by lazyart on 2006-10-24
I'm going to add to this just for future reference.

My 7820N went in without a hiccup.  I used the HP LaserJet PCL 6 driver in CUPS, also setting is up as an ipp printer. (Note: there are entries in CUPS for Hewlett-Packard and for HP.  Look under HP for the PCL6 driver.) Next I went to Brother's site and downloaded the brscan2 .deb package for scanning and it works like a champ in SANE.  This all on Dapper.

I haven't set up fax at this point.

---

### Post by jay5000 on 2007-02-11
I am using Edgy.  I had a similar problem.  I solved it by reinstalling most foomatic drivers.  Next time I tried to set up the printer using the Ubuntu Gnome interface the MFC 7820N script 3 driver appeared on the Brother setup. 

Reinstall or install most of the  foomatic drivers including those from Linux Printing
I have these foomatic drivers installed
foo2zjs
foomatic-db
foomatic-db-engine
foomatic-db-hpijs
foomatic-filters
foomatic-filters-ppds
hpijs
linuxprinting.org-ppds
min12xxw

I have these cupsys packages installed:
cupsys
cupsys-bsd
cupsys-client
cupsys-common
cupsys-driver-gutenprint
foomatic-filters
libcupsys2
libcupsys2-dev


Set up new printer Ubuntu System-> Administration=>Printing

URI: ipp://192.168.1.5/binary_p1

The MFC-7820N driver should show up

Then maybe want to setup cups using the web
[http://localhost:631](http://localhost:631)
NON ROOT user name
(password)

---

### Post by mattbphat on 2008-05-07
I recently purchased a MFC-7820N.  I spent a good 30-40 minutes installing the software on MS Vista before I could print.  

For Ubuntu Fiesty Fawn, I chose System->Admin->Printing and the printer was automatically detected...on the network!  I think that is pretty incredible. :)

One thing I did which may have made a difference is that I discovered the "logged in" to the web UI and changed the IP address to static and then added that IP and a name in my /etc/hosts file.

I'm about to try scanning.

Matt

---

### Post by al108 on 2008-05-13
Great news Matt! I was thinking of picking one up soon. Thanks for the report. Hopefully it works in Hardy too.

Here's some more info on setting it up [http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-MFC-7820N](http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-MFC-7820N)

---

