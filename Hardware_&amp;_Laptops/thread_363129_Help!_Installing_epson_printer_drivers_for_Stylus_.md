---
title: "Help! Installing epson printer drivers for Stylus Photo R260"
date: 2007-02-16
forum: Hardware &amp; Laptops
---

### Post by radtek on 2007-02-16
[FONT="Comic Sans MS"]I've tried to install the Epson linux drivers to no avail. I'm sure it is my lack of knowledge and inexperience that is creating the problem.

I downloaded and un-tarred the driver package. Opened in terminal and **sudo ./configure**

(I can provide the print-out if needed, but it is long... so ask and I'll post it.

Then **sudo make** and I get:

```
radtek@ubuntu:~/Desktop/pipslite-1.0.0$ sudo make
make  all-recursive
make[1]: Entering directory `/home/radtek/Desktop/pipslite-1.0.0'
Making all in libltdl
make[2]: Entering directory `/home/radtek/Desktop/pipslite-1.0.0/libltdl'
/bin/bash ./libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c ltdl.c
rm -f .libs/ltdl.lo
gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -c ltdl.c  -fPIC -DPIC -o .libs/ltdl.lo
gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -c ltdl.c -o ltdl.o >/dev/null 2>&1
mv -f .libs/ltdl.lo ltdl.lo
/bin/bash ./libtool --mode=link gcc  -g -O2  -o libltdlc.la   ltdl.lo -ldl 
rm -fr .libs/libltdlc.la .libs/libltdlc.* .libs/libltdlc.*
ar cru .libs/libltdlc.al ltdl.lo
ranlib .libs/libltdlc.al
creating libltdlc.la
(cd .libs && rm -f libltdlc.la && ln -s ../libltdlc.la libltdlc.la)
make[2]: Leaving directory `/home/radtek/Desktop/pipslite-1.0.0/libltdl'
Making all in src
make[2]: Entering directory `/home/radtek/Desktop/pipslite-1.0.0/src'
gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib   -DGS_PATH=\"gs\" -DLOCALEDIR=\"/usr/share/locale\" -DPRINTER_MODEL="\"LITE\"" -DLITE -DLIBPATH=\"/usr/lib/liblite.so\" -DRSC_PATH=\"/etc/pipsrc\" -DSPOOL_NAME=\"lite\" -DLOCALE_PATH=\"/usr/share/locale\" -DDATA_PATH=\"/usr/local/EPAva/LITE\" -DPRTOPT_PATH=\"/usr/local/EPAva/printer/prtOpt.csv\" -DPAPER_PATH=\"/usr/local/EPAva/printer/paper_list.csv\" -D_LPR_DIRECT -fsigned-char -DCUPS_FILTER_PATH=\"/usr/lib/cups/filter\" -g -O2 -Wall -c getstat.c
getstat.c:34:18: error: ltdl.h: No such file or directory
getstat.c: In function &#8216;get_printer_peculiar&#8217;:
getstat.c:141: error: &#8216;lt_dlhandle&#8217; undeclared (first use in this function)
getstat.c:141: error: (Each undeclared identifier is reported only once
getstat.c:141: error: for each function it appears in.)
getstat.c:141: error: expected &#8216;;&#8217; before &#8216;lib_h&#8217;
getstat.c:147: warning: implicit declaration of function &#8216;lt_dlinit&#8217;
getstat.c:150: warning: implicit declaration of function &#8216;lt_dlerror&#8217;
getstat.c:150: warning: passing argument 2 of &#8216;fprintf&#8217; makes pointer from integer without a cast
getstat.c:153: error: &#8216;lib_h&#8217; undeclared (first use in this function)
getstat.c:153: warning: implicit declaration of function &#8216;lt_dlopenext&#8217;
getstat.c:155: warning: passing argument 2 of &#8216;fprintf&#8217; makes pointer from integer without a cast
getstat.c:159: warning: implicit declaration of function &#8216;lt_dlsym&#8217;
make[2]: *** [getstat.o] Error 1
make[2]: Leaving directory `/home/radtek/Desktop/pipslite-1.0.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/radtek/Desktop/pipslite-1.0.0'
make: *** [all-recursive-am] Error 2
radtek@ubuntu:~/Desktop/pipslite-1.0.0$ 

```

Please help! Reportedly these drivers work.

Another thought- some of the "scripts?" in pipslite start with !** /bin/sh** instead of !** /bin/bash**. Could this be the source of my problem?

[/FONT]

---

### Post by chuckyp on 2007-03-04
Okay do you have build-essentials installed cuz it looks like gcc is missing.  Also availible from epson is the rpm package you may be able to just install that with alien.

---

### Post by ookadoo on 2007-03-17
Where can you find the Linux driver from Epson?  The only choices I see on the site are Windows and Mac.

The only choice that is close to R260 is R220 under Ubuntu's (Edgy) Add Printer feature.  Not sure if this is what I should use.

::EDIT::

I found the avasys page, avasys.jp but after trying to alien the RPMs printer still didn't work AND I received the error below after a restart, and some crazy things were happening with my apps.

"There was an error starting the GNOME Settings Daemon." and "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

I fixed this by remove --purging the package and then reinstalling everything gnome-related. :(  I still don't have icons on my desktop though, but I never used them anyway.

So then I tried to ./configure the source and got a "cups-config missing" error.  I installed libcupsys2-dev and got past ./configure.  Now I'm stuck at the following error.

gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib   -DGS_PATH=\"gs\" -DLOCALEDIR=\"/usr/share/locale\" -DPRINTER_MODEL="\"LITE\"" -DLITE -DLIBPATH=\"/usr/lib/liblite.so\" -DRSC_PATH=\"/etc/pipsrc\" -DSPOOL_NAME=\"lite\" -DLOCALE_PATH=\"/usr/share/locale\" -DDATA_PATH=\"/usr/local/EPAva/LITE\" -DPRTOPT_PATH=\"/usr/local/EPAva/printer/prtOpt.csv\" -DPAPER_PATH=\"/usr/local/EPAva/printer/paper_list.csv\" -D_LPR_DIRECT -fsigned-char -DCUPS_FILTER_PATH=\"/usr/lib/cups/filter\" -g -O2 -Wall -c getstat.c
getstat.c:34:18: error: ltdl.h: No such file or directory
getstat.c: In function &#8216;get_printer_peculiar&#8217;:
getstat.c:141: error: &#8216;lt_dlhandle&#8217; undeclared (first use in this function)
getstat.c:141: error: (Each undeclared identifier is reported only once
getstat.c:141: error: for each function it appears in.)
getstat.c:141: error: expected &#8216;;&#8217; before &#8216;lib_h&#8217;
getstat.c:147: warning: implicit declaration of function &#8216;lt_dlinit&#8217;
getstat.c:150: warning: implicit declaration of function &#8216;lt_dlerror&#8217;
getstat.c:150: warning: passing argument 2 of &#8216;fprintf&#8217; makes pointer from integer without a cast
getstat.c:153: error: &#8216;lib_h&#8217; undeclared (first use in this function)
getstat.c:153: warning: implicit declaration of function &#8216;lt_dlopenext&#8217;
getstat.c:155: warning: passing argument 2 of &#8216;fprintf&#8217; makes pointer from integer without a cast
getstat.c:159: warning: implicit declaration of function &#8216;lt_dlsym&#8217;
make[2]: *** [getstat.o] Error 1
make[2]: Leaving directory `/home/$me/Epson Driver/pipslite-1.0.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/$me/Epson Driver/pipslite-1.0.0'
make: *** [all-recursive-am] Error 2

Any help would be appreciated.  I have build-essentials installed as several c files were compiled successfully before this one returned the error.

:::EDIT AGAIN:::

I took the printer back shortly afterward.  I got it working but with a constantly running application.  It just didn't work out and the thing was a beast on my desk.  Good luck to anyone who wants to get the R260's working.

---

### Post by orion_oxotnik on 2008-02-06
I stumbled across this thread because I was having similar issues installing the avasys linux drivers for my Epson RX680. 

The problem the last person was having was due to this:
> getstat.c:34:18: error: ltdl.h: No such file or directory

To get past that you need to install **libltdl3-dev** and then run configure and make over again.
Only I also got more errors (a similar 'No such file' line for png.h and then cups/raster.h). Those required that I install **libpng12-dev**, **libcupsimage2-dev**, and** libcupsys2-dev**

After all of that, the avasys drivers finally 'made' cleanly. Only I'm not sure what I gained from it. There doesn't seem to be a clear next step. No new options show up for print drivers (I'm still stuck using the RX640 drivers for now).

---

### Post by gorean on 2008-03-11
I don't remember where I got this file but it exists and is freeware.
EPSON_Stylus_Photo_R260_USB_1.ppd
I just tried a google search for it and nothing.  I only looked for it when an upgrade to one of my systems lost the config for me.  I would be happy to post it somewhere.  I haven't tried to print any photos or cds but in general I have found no fault with it for everyday printing.
Following are the first lines of the file.

*PPD-Adobe: "4.3"
*% PPD file for CUPS/Gutenprint.
*% Copyright 1993-2006 by Easy Software Products and Robert Krawitz.
*% This program is free software; you can redistribute it and/or
*% modify it under the terms of the GNU General Public License,
*% version 2, as published by the Free Software Foundation.
*%
*% This program is distributed in the hope that it will be useful, but
*% WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY
*% or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License
*% for more details.
*%
*% You should have received a copy of the GNU General Public License
*% along with this program; if not, write to the Free Software
*% Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA.
*%
I think I had to install Gutenprint (or rather Gimp Print) and then put the file at /etc/cups/ppd.

---

