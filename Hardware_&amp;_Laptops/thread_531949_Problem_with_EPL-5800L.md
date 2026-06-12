---
title: "Problem with EPL-5800L"
date: 2007-08-22
forum: Hardware &amp; Laptops
---

### Post by Stephen Ong on 2007-08-22
Just installed Edubuntu 7.04 but could not find the driver for my Epson EPL-5800L printer.

I am new to Linux, where can I get the driver ans how to install it ?

---

### Post by linuxwizard on 2007-08-22
According to this that printer mostly works
[http://www.openprinting.org/show_printer.cgi?recnum=Epson-EPL-5800L](http://www.openprinting.org/show_printer.cgi?recnum=Epson-EPL-5800L)

Start here to get to driver/ follow instructions
[http://epsonepl.sourceforge.net/](http://epsonepl.sourceforge.net/)



 Mostly 
    These printers work almost perfectly - funny enhanced resolution modes may be missing, or the color is a bit off, but nothing that would make the printouts not useful.

---

### Post by Stephen Ong on 2007-08-25
downloaded the file as instructed but had problem when I execute the line "./configure"
my system is a fresh kubuntu installation

stephen@stephen-desktop:~$ tar -zxvf epsoneplijs-0.4.0.tgz 
epsoneplijs-0.4.0/
epsoneplijs-0.4.0/CVS/
epsoneplijs-0.4.0/CVS/Root
epsoneplijs-0.4.0/CVS/Repository
epsoneplijs-0.4.0/CVS/Entries
epsoneplijs-0.4.0/apsfilter/
epsoneplijs-0.4.0/apsfilter/CVS/
epsoneplijs-0.4.0/apsfilter/CVS/Root
epsoneplijs-0.4.0/apsfilter/CVS/Repository
epsoneplijs-0.4.0/apsfilter/CVS/Entries
epsoneplijs-0.4.0/apsfilter/epsonepl.apsfilter
epsoneplijs-0.4.0/ChangeLog
epsoneplijs-0.4.0/FAQ
epsoneplijs-0.4.0/LIMITATIONS
epsoneplijs-0.4.0/Makefile.in
epsoneplijs-0.4.0/README
epsoneplijs-0.4.0/README.FlowControl
epsoneplijs-0.4.0/README.foomatic
epsoneplijs-0.4.0/README.ijs
epsoneplijs-0.4.0/common.mak
epsoneplijs-0.4.0/configure
epsoneplijs-0.4.0/configure.in
epsoneplijs-0.4.0/epl_57interpret.c
epsoneplijs-0.4.0/epl_59interpret.c
epsoneplijs-0.4.0/epl_bid.h
epsoneplijs-0.4.0/epl_bid_replies.c
epsoneplijs-0.4.0/epl_bid_utils.c
epsoneplijs-0.4.0/epl_compress.c
epsoneplijs-0.4.0/epl_compress.h
epsoneplijs-0.4.0/epl_config.h
epsoneplijs-0.4.0/epl_job.h
epsoneplijs-0.4.0/epl_job_footer.c
epsoneplijs-0.4.0/epl_job_header.c
epsoneplijs-0.4.0/epl_page_footer.c
epsoneplijs-0.4.0/epl_page_header.c
epsoneplijs-0.4.0/epl_poll.c
epsoneplijs-0.4.0/epl_print_stripe.c
epsoneplijs-0.4.0/epl_status.c
epsoneplijs-0.4.0/epl_test.ps
epsoneplijs-0.4.0/epl_test.sh
epsoneplijs-0.4.0/epl_utils_kusb.c
epsoneplijs-0.4.0/epl_utils_libieee1284.c
epsoneplijs-0.4.0/epl_utils_libusb.c
epsoneplijs-0.4.0/epl_write.c
epsoneplijs-0.4.0/ijs-config.in
epsoneplijs-0.4.0/ijs.c
epsoneplijs-0.4.0/ijs.h
epsoneplijs-0.4.0/ijs_client.c
epsoneplijs-0.4.0/ijs_client.h
epsoneplijs-0.4.0/ijs_client_example.c
epsoneplijs-0.4.0/ijs_exec_unix.c
epsoneplijs-0.4.0/ijs_exec_win.c
epsoneplijs-0.4.0/ijs_server.c
epsoneplijs-0.4.0/ijs_server.h
epsoneplijs-0.4.0/ijs_server_epsonepl.c
epsoneplijs-0.4.0/ijs_server_example.c
epsoneplijs-0.4.0/ijs_spec.pdf
epsoneplijs-0.4.0/ijs_spec.sgml
epsoneplijs-0.4.0/install-sh
epsoneplijs-0.4.0/ps2epl
epsoneplijs-0.4.0/ps2epl.pl
epsoneplijs-0.4.0/state.eps
epsoneplijs-0.4.0/state.fig
epsoneplijs-0.4.0/test5700lusb.c
epsoneplijs-0.4.0/unistd_.h
epsoneplijs-0.4.0/unix.mak
epsoneplijs-0.4.0/windows.mak
epsoneplijs-0.4.0/cups/
epsoneplijs-0.4.0/cups/CVS/
epsoneplijs-0.4.0/cups/CVS/Root
epsoneplijs-0.4.0/cups/CVS/Repository
epsoneplijs-0.4.0/cups/CVS/Entries
epsoneplijs-0.4.0/cups/00_README
epsoneplijs-0.4.0/cups/Epson-EPL-5700L-epl5700l-cups.ppd.gz
epsoneplijs-0.4.0/cups/Epson-EPL-5700L-epl5700l.ppd.gz
epsoneplijs-0.4.0/cups/Epson-EPL-5700L-epl5700lusb-cups.ppd.gz
epsoneplijs-0.4.0/cups/Epson-EPL-5700L-epl5700lusb.ppd.gz
epsoneplijs-0.4.0/cups/Epson-EPL-5800L-epl5800l-cups.ppd.gz
epsoneplijs-0.4.0/cups/Epson-EPL-5800L-epl5800l.ppd.gz
epsoneplijs-0.4.0/cups/Epson-EPL-5900L-epl5900l-cups.ppd.gz
epsoneplijs-0.4.0/cups/Epson-EPL-5900L-epl5900l.ppd.gz
epsoneplijs-0.4.0/cups/contrib-Debian-3.0-1.eml
epsoneplijs-0.4.0/cups/contrib-Makdrake-9.0-5700L-1.eml
epsoneplijs-0.4.0/cups/contrib-Makdrake-9.0-5700L-2.eml
epsoneplijs-0.4.0/cups/contrib-SuSE-8.0-5700L-1.eml
epsoneplijs-0.4.0/cups/contrib-SuSE-8.0-5700L-2.eml
epsoneplijs-0.4.0/epl_docs/
epsoneplijs-0.4.0/epl_docs/CVS/
epsoneplijs-0.4.0/epl_docs/CVS/Root
epsoneplijs-0.4.0/epl_docs/CVS/Repository
epsoneplijs-0.4.0/epl_docs/CVS/Entries
epsoneplijs-0.4.0/epl_docs/README.1st
epsoneplijs-0.4.0/epl_docs/epl-5700.c
epsoneplijs-0.4.0/epl_docs/epl-5800.c
epsoneplijs-0.4.0/epl_docs/epl-protocol.pdf
epsoneplijs-0.4.0/epl_docs/epl5x00l.c
epsoneplijs-0.4.0/epl_docs/message.eml
epsoneplijs-0.4.0/foomatic/
epsoneplijs-0.4.0/foomatic/CVS/
epsoneplijs-0.4.0/foomatic/CVS/Root
epsoneplijs-0.4.0/foomatic/CVS/Repository
epsoneplijs-0.4.0/foomatic/CVS/Entries
epsoneplijs-0.4.0/foomatic/driver/
epsoneplijs-0.4.0/foomatic/driver/CVS/
epsoneplijs-0.4.0/foomatic/driver/CVS/Root
epsoneplijs-0.4.0/foomatic/driver/CVS/Repository
epsoneplijs-0.4.0/foomatic/driver/CVS/Entries
epsoneplijs-0.4.0/foomatic/driver/epl5700l.xml
epsoneplijs-0.4.0/foomatic/driver/epl5800l.xml
epsoneplijs-0.4.0/foomatic/driver/epl5900l.xml
epsoneplijs-0.4.0/foomatic/driver/epl6100l.xml
epsoneplijs-0.4.0/foomatic/driver/epl6200l.xml
epsoneplijs-0.4.0/foomatic/opt/
epsoneplijs-0.4.0/foomatic/opt/CVS/
epsoneplijs-0.4.0/foomatic/opt/CVS/Root
epsoneplijs-0.4.0/foomatic/opt/CVS/Repository
epsoneplijs-0.4.0/foomatic/opt/CVS/Entries
epsoneplijs-0.4.0/foomatic/opt/epsonepl-Density.xml
epsoneplijs-0.4.0/foomatic/opt/epsonepl-Dpi.xml
epsoneplijs-0.4.0/foomatic/opt/epsonepl-FlowControl.xml
epsoneplijs-0.4.0/foomatic/opt/epsonepl-PageSize.xml
epsoneplijs-0.4.0/foomatic/opt/epsonepl-Ritech.xml
epsoneplijs-0.4.0/foomatic/opt/epsonepl-TonerSave.xml
epsoneplijs-0.4.0/foomatic/printer/
epsoneplijs-0.4.0/foomatic/printer/CVS/
epsoneplijs-0.4.0/foomatic/printer/CVS/Root
epsoneplijs-0.4.0/foomatic/printer/CVS/Repository
epsoneplijs-0.4.0/foomatic/printer/CVS/Entries
epsoneplijs-0.4.0/foomatic/printer/312297.xml
epsoneplijs-0.4.0/foomatic/printer/Epson-EPL-5800L.xml
epsoneplijs-0.4.0/foomatic/printer/Epson-EPL-5900L.xml
epsoneplijs-0.4.0/foomatic/printer/Epson-EPL-6100L.xml
epsoneplijs-0.4.0/foomatic/printer/Epson-EPL-6200L.xml
epsoneplijs-0.4.0/foomatic_PPDs/
epsoneplijs-0.4.0/foomatic_PPDs/CVS/
epsoneplijs-0.4.0/foomatic_PPDs/CVS/Root
epsoneplijs-0.4.0/foomatic_PPDs/CVS/Repository
epsoneplijs-0.4.0/foomatic_PPDs/CVS/Entries
epsoneplijs-0.4.0/foomatic_PPDs/Epson-EPL-5700L-epl5700l-cups.ppd.gz
epsoneplijs-0.4.0/foomatic_PPDs/Epson-EPL-5800L-epl5800l-cups.ppd.gz
epsoneplijs-0.4.0/foomatic_PPDs/Epson-EPL-5900L-epl5900l-cups.ppd.gz
epsoneplijs-0.4.0/foomatic_PPDs/Epson-EPL-6100L-epl6100l-cups.ppd.gz
epsoneplijs-0.4.0/foomatic_PPDs/Epson-EPL-6200L-epl6200l-cups.ppd.gz
epsoneplijs-0.4.0/foomatic_scripts/
epsoneplijs-0.4.0/foomatic_scripts/CVS/
epsoneplijs-0.4.0/foomatic_scripts/CVS/Root
epsoneplijs-0.4.0/foomatic_scripts/CVS/Repository
epsoneplijs-0.4.0/foomatic_scripts/CVS/Entries
epsoneplijs-0.4.0/foomatic_scripts/install_customfoomatic
epsoneplijs-0.4.0/foomatic_scripts/install_mandrake
epsoneplijs-0.4.0/foomatic_scripts/install_redhat8
epsoneplijs-0.4.0/foomatic_scripts/install_redhat9
epsoneplijs-0.4.0/foomatic_scripts/install_debian
epsoneplijs-0.4.0/epl_utils_null.c
epsoneplijs-0.4.0/epl_time.c
epsoneplijs-0.4.0/epl_time.h
epsoneplijs-0.4.0/epsoneplijs.spec
epsoneplijs-0.4.0/epl_62interpret.c
stephen@stephen-desktop:~$ cd epsoneplijs-0.4.0/
stephen@stephen-desktop:~/epsoneplijs-0.4.0$ ./configure 
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
stephen@stephen-desktop:~/epsoneplijs-0.4.0$ make
make: *** No targets specified and no makefile found.  Stop.
stephen@stephen-desktop:~/epsoneplijs-0.4.0$

---

### Post by hounddog on 2007-09-11
I have the same problem with my EPL-6100L printer.  It would be very nice if the next version of Ubuntu will provide support for our printers so we wouldn't have to mess around with compiling drivers or force downgrading deb-packages, yay!!!

---

### Post by acumos on 2007-10-16
All EPL-xxxxL series seem to be "winprint". This means that they can work properly only in winzoz.

---

### Post by hounddog on 2007-10-19
My EPL-6100L printer prints fantastically under PCLinuxOS.  So it is not as if the printer is not supported by Linux.  It's just Ubuntu that it doesn't work with.  Actually, it doesn't work with Fedora either and I haven't tried the other distros.

---

### Post by Cubsh on 2008-02-24
Before executing the line "./configure" the "build-essential" metapackage must be installed.

---

