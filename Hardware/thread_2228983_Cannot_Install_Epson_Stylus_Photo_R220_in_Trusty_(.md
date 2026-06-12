---
title: "Cannot Install Epson Stylus Photo R220 in Trusty (amd64)"
date: 2014-06-10
forum: Hardware
---

### Post by lambdafox on 2014-06-10
[FONT=arial black]I am trying to set up my printer in Ubuntu GNOME 14.04 (amd64).

When I use Applications-System Settings-Printers and click on the plus button to add a printer, the add new printer dialogue pops up and identifies my printer correctly.

When I highlight it and click the add button, it says it is searching for drivers, it finds them and changes the status to installing.  It stays in this state for several minutes and always concludes with an error that it failed to install printer.

I went to the epson web site and downloaded the recommended linux driver from there.  

the driver has to be ./configure, make, make install -ed

When I run, ./configure in the directory where the source is, I get the following output.  I have edited out all the lines that are obviously ok to me as a linux noob. I already got rid of some of the problems I found, like it wanted bison  installed and I did that.  These are the things I just have no idea what  or if I need to do something about. These are the ones that I am either not sure about or look suspect to me:
[/FONT]
[FONT=arial narrow]./configure
...
checking whether -lc should be explicitly linked in... no
creating libtool
...
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... (cached) yes
checking for working vfork... (cached) yes
...
checking whether gcc needs -traditional... no
...
checking return type of signal handlers... void
...
checking for iconv declaration... 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
...
checking whether included gettext is requested... no
...
checking whether to enable maintainer-specific portions of Makefiles... no
...
checking whether the C compiler (gcc  ) is a cross-compiler... no
...
checking for Cygwin environment... no
checking for mingw32 environment... no

...
checking for executable suffix... no
...
checking whether -lc should be explicitly linked in... no
...
checking for opendir in -ldir... no
checking whether gcc supports assert without backlinking... 
...
checking for shl_load... no
checking for shl_load in -ldld... no
...
checking for _ prefix in compiled symbols... no
...
checking for dl.h... no
checking for sys/dl.h... no
checking for dld.h... no[/FONT]

[FONT=arial black]and make returns this:
[/FONT]
 [FONT=arial narrow]make
make  all-recursive
make[1]: Entering directory `/home/randyb/Downloads/pips-spr220-2.6.3'
Making all in libltdl
make[2]: Entering directory `/home/randyb/Downloads/pips-spr220-2.6.3/libltdl'
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
make[2]: Leaving directory `/home/randyb/Downloads/pips-spr220-2.6.3/libltdl'
Making all in src
make[2]: Entering directory `/home/randyb/Downloads/pips-spr220-2.6.3/src'
gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include    -DGS_PATH=\"gs\" -DLOCALEDIR=\"/usr/share/locale\" -DPRINTER_MODEL="\"Stylus Photo R220\"" -DSPR220 -DLIBPATH=\"/usr/lib/libspr220.so\" -DRSC_PATH=\"/etc/pipsrc\" -DSPOOL_NAME=\"spr220\" -DLOCALE_PATH=\"/usr/share/locale\" -DNAVI_PATH=\"/usr/bin/ekpnavi\" -DDATA_PATH=\"/usr/local/EPKowa/SPR220\" -DRULED_PATH=\"/usr/local/EPKowa/SPR220/BID.PRN\" -DPATCH_PATH=\"/usr/local/EPKowa/SPR220/PATCH.PRN\" -DBAND_PATH=\"/usr/local/EPKowa/SPR220/BAND.PRN\" -DCUT_PATH=\"/usr/local/EPKowa/SPR220/CUT.PRN\" -D_LPR_DIRECT -fsigned-char -DCUPS_FILTER_PATH=\"/usr/lib/cups/filter\" -g -O2 -Wall -c rastertopips.c
rastertopips.c:42:13: error: &#8216;NAME_MAX&#8217; undeclared here (not in a function)
  char model[NAME_MAX + 1];
             ^
rastertopips.c: In function &#8216;main&#8217;:
rastertopips.c:137:2: warning: &#8216;cupsRasterReadHeader&#8217; is deprecated (declared at /usr/include/cups/raster.h:370): Use cupsRasterReadHeader2 instead. [-Wdeprecated-declarations]
  while (cupsRasterReadHeader (ras, &header))
  ^
rastertopips.c:175:4: warning: pointer targets in passing argument 2 of &#8216;cupsRasterReadPixels&#8217; differ in signedness [-Wpointer-sign]
    if (!cupsRasterReadPixels (ras, image_raw, header.cupsBytesPerLine))
    ^
In file included from rastertopips.c:26:0:
/usr/include/cups/raster.h:372:18: note: expected &#8216;unsigned char *&#8217; but argument is of type &#8216;char *&#8217;
 extern unsigned  cupsRasterReadPixels(cups_raster_t *r,
                  ^
rastertopips.c: In function &#8216;kill_pips&#8217;:
rastertopips.c:365:10: warning: ignoring return value of &#8216;system&#8217;, declared with attribute warn_unused_result [-Wunused-result]
   system (syscommand);
          ^
make[2]: *** [rastertopips.o] Error 1
make[2]: Leaving directory `/home/randyb/Downloads/pips-spr220-2.6.3/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/randyb/Downloads/pips-spr220-2.6.3'
make: *** [all-recursive-am] Error 2
[/FONT]

---

### Post by pdc on 2014-06-11
hi lambdafox;

usually one can point folks to the Epson driver; however they only provided rpm packages then (back in 2005) 

if one looks in Open Printing [http://www.openprinting.org/printer/Epson/Epson-Stylus_Photo_R240](http://www.openprinting.org/printer/Epson/Epson-Stylus_Photo_R240)

your R220 is not listed but the epson-escpr is said to work perfectly: if you click to download the Debian 64bit version, hopefully it will behave itself and install for you; you need to package which ends ..............amd64.deb      (Ubuntu uses debian packages so you need a debian package ..)

please let us know how you get along

---

### Post by Mark Phelps on 2014-06-11
When I last used my Epson R220, I was able to get it installed and working using CUPS.  You should try that.

---

### Post by lambdafox on 2014-06-11
I found a gutenprint driver on openprinting.org.  I have installed the supporting software for gutenpprint on ubuntu.  Unfortunately, when I try to go to localhost:631 in firefox to add the printer, I get a box saying Authentication is required

A username and password are being requested by [http://localhost:631](http://localhost:631). The site says: "CUPS"

I tried my ubuntu username and password, but that does not let me finish.

I get:

Unauthorized

Enter your username and password or the root username and password to  access this page. If you are using Kerberos authentication, make sure  you have a valid Kerberos ticket.

I have tried user name "root" with my password and my username with my password and the results are the same

UPDATE:  I was able to fix this by creating a password for the root user and then retrying with 'root' as the user and the new password.

---

### Post by pdc on 2014-06-12
so you can attempt to add a new printer registration with CUPS: 

if you can now be allowed into CUPS, you can add a new entry for your R220;

it should show up as a local printer......it is usb?? the prompts will lead you through a series of screens

---

