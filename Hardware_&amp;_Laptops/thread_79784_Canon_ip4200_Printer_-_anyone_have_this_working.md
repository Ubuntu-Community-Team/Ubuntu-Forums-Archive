---
title: "Canon ip4200 Printer - anyone have this working?"
date: 2005-10-20
forum: Hardware &amp; Laptops
---

### Post by phillytim on 2005-10-20
hey everyone - this is my first dip into UBUNTU, and i'm loving it!  my background in linux has extended back to 1997 with the redhat/fedora stuff, but the buzz about UBUNTU has caused me to change here.

i have a new canon pixma **ip4200** printer, and it doesn't have drivers to run.  i know there are some threads about getting the ip4000 to run in linux with some of canon's japanese drivers.  

but what about the **ip4200** - does anyone have it?  if so, how do you have yours working?

---

### Post by nysmo on 2005-10-22
I have also a ip4200. And it is working great on breezy. It recognized it right away and I only needed to choose the bjj-4200 driver. Don´t know about hoary but it shouldn´t be to hard to get the driver there.

---

### Post by 4x4 on 2005-11-22
WORKING :-) ubuntu breezy
type: bjc-4200    driver: bjc-600 (recommended)
writeingport:choose usb-port 1 (working for me)

sorry my bad english

---

### Post by chorltonian on 2005-11-28
That BJ4200 driver mentioned by some is for an ancient bubble jet printer and supports a maximum res of 360 dpi - I just tried it, thinking maybe I had it wrong all along. No, this driver is useless with this printer, the test page comes out like a postage stamp.

The only way to get good support for all the features, hi res, duplexing, decent photo reproduction etc., is to buy turboprint. Its not very expensive at about 20 uk pounds but I tried all sorts of stuff before I finally gave in and decided to buy it.

---

### Post by Junkmaster357 on 2006-02-15
I'm using the Ubuntu AMD 64 bit.  I'm totally new to Ubuntu, and so far I love it.

I have a Canon PIXMA iP4200 Photo Printer, and I have absolutely no clue how to get it to work in Ubuntu.

Could someone please be kind enough to help me out here?

---

### Post by henwyn on 2006-04-09
The Canon iP 4200 works well using Turboprint.  There is a free version you can try, but it will print a Turboprint logo on your pages until it is licensed.  People using Ubuntu should download the .tgz file, move it to where you want to install it, (probably your /home/? directory) and expand it.  If you are licensing it, pay for it in their store and download the license file to the directory created when you expanded the .tgz file.  Then execute the install.sh file in that directory.  This is traditionally done from a terminal window.  Once it is installed, configure your printer and it should work.  If you should want to uninstall this software in the future, there is an uninstall.sh file in the same directory which is supposed to take care of that chore.  I haven't personally tried this, but everything else works as advertised.

Be advised, however that there is currently a bug in Dapper Drake which causes Canon printers with a USB hookup using Turboprint or Gutenprint drivers to malfunction; printing stalls partway through a page and things hang.  Reinstalling an earlier version of cups seems to fix it.

HTH.  Let me know if you need more info.

---

### Post by groggo on 2006-04-28
canon bj4400 driver works fine on my pixima 5000

---

### Post by mschievano on 2006-05-02
myne don't work.
how this 4200 can work well? I also try to install the ppd file from japan , but nothing

---

### Post by Shadow Slasher on 2006-05-05
You should be able to download the  linux drivers from Canon (cheers to Canon to being forward thinking) from their Japanese website.

Try here:

[http://cweb.canon.jp/drv-upd/bj/other.html](http://cweb.canon.jp/drv-upd/bj/other.html)

They are called "Filters" rather than drivers.

- SS

---

### Post by Jose Catre-Vandis on 2006-05-06
Nice find Shadowslasher :-)

Here are the three files you need, please report back on success?

[http://download.canon.jp/pub/driver/bj/linux/cnijfilter-ip4200-2.60-1.i386.rpm](http://download.canon.jp/pub/driver/bj/linux/cnijfilter-ip4200-2.60-1.i386.rpm)
[http://download.canon.jp/pub/driver/bj/linux/cnijfilter-ip4200-lprng-2.60-1.i386.rpm](http://download.canon.jp/pub/driver/bj/linux/cnijfilter-ip4200-lprng-2.60-1.i386.rpm)
[http://download.canon.jp/pub/driver/bj/linux/guideip4200-2.60-1.tar.gz](http://download.canon.jp/pub/driver/bj/linux/guideip4200-2.60-1.tar.gz)

---

### Post by mschievano on 2006-05-13
[QUOTE=Jose Catre-Vandis]Nice find Shadowslasher :-)

Here are the three files you need, please report back on success?

[http://download.canon.jp/pub/driver/bj/linux/cnijfilter-ip4200-2.60-1.i386.rpm](http://download.canon.jp/pub/driver/bj/linux/cnijfilter-ip4200-2.60-1.i386.rpm)
[http://download.canon.jp/pub/driver/bj/linux/cnijfilter-ip4200-lprng-2.60-1.i386.rpm](http://download.canon.jp/pub/driver/bj/linux/cnijfilter-ip4200-lprng-2.60-1.i386.rpm)
[http://download.canon.jp/pub/driver/bj/linux/guideip4200-2.60-1.tar.gz](http://download.canon.jp/pub/driver/bj/linux/guideip4200-2.60-1.tar.gz)[/QUOTE]


I had try also this.
no good :-k

---

### Post by mschievano on 2006-05-21
also because i have the 64 bit of dapper drake ...

---

### Post by gotaug on 2006-05-31
I was able to convert the .rpm's to .deb with alien, and then I manually copied them to the corresponding locations in the usr folder...

CUPS found the new printer driver immediately and gave appropriate options (duplex printing), but wouldn't print a test page.

I'm a newbie, so this is as far as I got.  The printer doesn't even twitch when you send it a job.  I'm using DapperRC AMD64, and would appreciate any help available.

---

### Post by Cimmo on 2006-06-04
I have tried also this new driver, but no print at all.
The printer is shown in cupsys, I can add it, but it didn't work.
Jobs stay in the queue and a red X is displayed over my printer in kde print.

Can be cupsys 1.2?

---

### Post by lrjx10a on 2006-06-06
Having the same problem as Cimmo ang gotaug, please somebody help:(

---

### Post by jgdumont on 2006-06-07
Hi,

I've mine working under Fedora core 5. I got my drivers from the normal site from canon. I just went to the download aeria selected, my printer model and selected linux as os. Then the drivers could be downloaded. 
Don't forget to look in the "doc" folder for some explanation.

---

### Post by lakelovers on 2006-06-07
There seems to be a lot of printer problems with Dapper. I have a Canon i560 and a TurboPrint driver that has worked in Hoary and Breezy and before that in Mandriva. I can't get Cups to see Turboprint. I first thought that I had lost the TurboPint keyfile but I asked for and got a new one. That didn't solve my problem. Has anybody got TurboPrint drive working in Dapper? If so, how did you do it?
Jerry

---

### Post by blueball on 2006-06-09
It took me 2 days of installing, and deinstalling, and reinstalling, but now it works great.

[http://software.canon-europe.com/](http://software.canon-europe.com/)
[http://software.canon-europe.com/files/soft24302/software/iP4200_Linux_260.tar.gz](http://software.canon-europe.com/files/soft24302/software/iP4200_Linux_260.tar.gz)
[http://software.canon-europe.com/files/soft24302/manual/guideip4200-2.60-1.tar.gz](http://software.canon-europe.com/files/soft24302/manual/guideip4200-2.60-1.tar.gz)

Thanks to Canon for the new drivers.

Red X: the printer might be stopped.

---

### Post by IbeeX on 2006-06-14
[QUOTE=blueball]It took me 2 days of installing, and deinstalling, and reinstalling, but now it works great.

[http://software.canon-europe.com/](http://software.canon-europe.com/)
[http://software.canon-europe.com/files/soft24302/software/iP4200_Linux_260.tar.gz](http://software.canon-europe.com/files/soft24302/software/iP4200_Linux_260.tar.gz)
[http://software.canon-europe.com/files/soft24302/manual/guideip4200-2.60-1.tar.gz](http://software.canon-europe.com/files/soft24302/manual/guideip4200-2.60-1.tar.gz)

Thanks to Canon for the new drivers.

Red X: the printer might be stopped.[/QUOTE]

I have 64 bit ubuntu? And how did you install them?

---

### Post by michaeljt on 2006-09-03
I added some experimental code to Gutenprint to support the iP4200.  It is in CVS, but not yet in any release version.  Anyone who feels like trying it out (and giving feedback if anything does not work!) is more than welcome.

---

### Post by IbeeX on 2006-09-04
> **michaeljt said:**
> I added some experimental code to Gutenprint to support the iP4200.  It is in CVS, but not yet in any release version.  Anyone who feels like trying it out (and giving feedback if anything does not work!) is more than welcome.
When I try to compile it from CVS I get this error message

make[2]: Entering directory `/home/ibrkanac/src/guten/print/doc/developer'
if test . = '.' ; then \
          : ; \
        else \
          for file in copying.xml dither.xml escp2.xml gutenprint.xml gpl-appendix.xml introduction.xml new-printer.xml problems.xml using.xml weave.xml ; do \
            if test -L $file ; then \
              rm -f $file ; \
            fi ; \
            ln -s -f ./$file $file ; \
          done ; \
        fi
gutenprint.xml
/bin/bash: gutenprint.xml: command not found
make[2]: *** [html-stamp] Error 127
make[2]: Leaving directory `/home/ibrkanac/src/guten/print/doc/developer'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/ibrkanac/src/guten/print/doc'
make: *** [install-recursive] Error 1


I hawe amd64 ubuntu 6.06

Ivan

---

### Post by michaeljt on 2006-09-06
Ivan,

that is a problem making the documentation.  If you've got that far, then the programmes have been made, and you can just do a

sudo make install

to install everything onto your system.  You will get an error message there as well, but everything you need should still work.

Regards,

Michael

---

### Post by IbeeX on 2006-09-09
OK then I tried tu setup printer using pixma 4000 HQ image gutenprint driver (is this right), and when I prit test page I get color output wrong all color inks look like they re out off fase to the right!

Is there anything I can do to correct or help?

---

### Post by michaeljt on 2006-09-11
If you have successfully installed the CVS version of Gutenprint, there should now be a Pixma iP4200 driver shown in the list.  You should use that, not the iP4000 driver.

---

### Post by IbeeX on 2006-09-11
> **IbeeX said:**
> When I try to compile it from CVS I get this error message

make[2]: Entering directory `/home/ibrkanac/src/guten/print/doc/developer'
if test . = '.' ; then \
          : ; \
        else \
          for file in copying.xml dither.xml escp2.xml gutenprint.xml gpl-appendix.xml introduction.xml new-printer.xml problems.xml using.xml weave.xml ; do \
            if test -L $file ; then \
              rm -f $file ; \
            fi ; \
            ln -s -f ./$file $file ; \
          done ; \
        fi
gutenprint.xml
/bin/bash: gutenprint.xml: command not found
make[2]: *** [html-stamp] Error 127
make[2]: Leaving directory `/home/ibrkanac/src/guten/print/doc/developer'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/ibrkanac/src/guten/print/doc'
make: *** [install-recursive] Error 1


I hawe amd64 ubuntu 6.06

Ivan


This is what I get try to do
"sudo make install", so I guess then driver are not installed since I don't see pixima ip 4200 driver

---

### Post by michaeljt on 2006-09-11
Does the file

print/src/cups/rastertogutenprint.5.0

exist?  Is it identical to

/usr/lib/cups/filter/rastertogutenprint.5.0?

---

### Post by IbeeX on 2006-09-11
> **michaeljt said:**
> Does the file

print/src/cups/rastertogutenprint.5.0

exist?  Is it identical to

/usr/lib/cups/filter/rastertogutenprint.5.0?
I only hawe this

ibrkanac@ibee:~/src/guten/print$ locate rastertogutenprint
/usr/lib/cups/filter/rastertogutenprint.5.0
ibrkanac@ibee:~/src/guten/print$ ls
ABOUT-NLS       config.h       COPYING                  doc-pak  m4local      NEWS     stamp-h1
aclocal.m4      config.h.in    cups-gutenprint.list     include  Makefile     po       test
AUTHORS         config.log     cups-gutenprint.list.in  INSTALL  Makefile.am  README
autogen.sh      config.status  CVS                      libtool  Makefile.in  samples
autom4te.cache  configure      de-scription-pak          m4       man          scripts
ChangeLog       configure.ac   doc                      m4extra  Matgen       src

Also I hawe driver iP4200-Ver2.60 standard only thing is that it don't work at all

---

### Post by michaeljt on 2006-09-12
If Gutenprint installed correctly, you should have a file called

/usr/share/cups/model/gutenprint/5.0/C/stp-bjc-PIXMA-iP4200.5.0.ppd.gz

A question: did you have gutenprint installed before you tried to install the CVS version (quite likely)?  If so, you might want to try uninstalling the debian package and try reinstalling the CVS one with

```
sudo make install
```

Another good test is to do

```
grep iP4200 /usr/sbin/cups-genppd.5.0
```

which should give the following output:

Binary file /usr/sbin/cups-genppd.5.0 matches

---

### Post by IbeeX on 2006-09-13
> **michaeljt said:**
> If Gutenprint installed correctly, you should have a file called

/usr/share/cups/model/gutenprint/5.0/C/stp-bjc-PIXMA-iP4200.5.0.ppd.gz

A question: did you have gutenprint installed before you tried to install the CVS version (quite likely)?  If so, you might want to try uninstalling the debian package and try reinstalling the CVS one with

```
sudo make install
```

Another good test is to do

```
grep iP4200 /usr/sbin/cups-genppd.5.0
```

which should give the following output:

Binary file /usr/sbin/cups-genppd.5.0 matches

No I don't hawe anything I also removed debian package guten-print and run @sudo make install" and same thing happened

make[2]: *** [html-stamp] Error 127
make[2]: Leaving directory `/home/ibrkanac/src/guten/print/doc/developer'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/ibrkanac/src/guten/print/doc'
make: *** [install-recursive] Error 1

---

### Post by michaeljt on 2006-09-13
OK, then try editing Makefile in the print/ directory and removing the word "doc" from the line

```
SUBDIRS = include src samples test po man doc scripts
```

---

### Post by mschievano on 2006-09-13
sorry, I don't understand if someone with dapper 64 bit make the printer work... and if yes what I have to download. Thanks

---

### Post by michaeljt on 2006-09-13
If you get the CVS version of Gutenprint (follow the instructions on [http://sourceforge.net/cvs/?group_id=1537)](http://sourceforge.net/cvs/?group_id=1537)), then build it and install it according to the instructions, that should let you use your iP4200.

Before you run autogen.sh to build it, you should change the line

```

SUBDIRS = include src samples test po man doc scripts

```

in the file print/Makefile.am and remove "doc" from it (or in print/Makefile if you have already run autogen.sh).  You should remove your gutenprint package before installing.

Sometime, gutenprint 5.0.1 should be released, and that will contain the iP4200 driver.  You could wait for that if you are not comfortable building yourself.

---

### Post by mschievano on 2006-09-14
> **michaeljt said:**
> If you get the CVS version of Gutenprint (follow the instructions on [http://sourceforge.net/cvs/?group_id=1537)](http://sourceforge.net/cvs/?group_id=1537)), then build it and install it according to the instructions, that should let you use your iP4200.

Before you run autogen.sh to build it, you should change the line

```

SUBDIRS = include src samples test po man doc scripts

```

in the file print/Makefile.am and remove "doc" from it (or in print/Makefile if you have already run autogen.sh).  You should remove your gutenprint package before installing.

Sometime, gutenprint 5.0.1 should be released, and that will contain the iP4200 driver.  You could wait for that if you are not comfortable building yourself.

thanks for the reply.
A last question: in
 cvs -z3 -d:pserver:anonymous@gimp-print.cvs.sourceforge.net:/cvsroot/gimp-print co -P modulename
what I have to put instead of modulename? :-\" 
thanks

(when I click on web viewer an error appear:
An Exception Has Occurred

The root "gimp-print" is unknown. If you believe the value is correct, then please double-check your configuration.

HTTP Response Status

404 Repository not found)

---

### Post by michaeljt on 2006-09-15
Substitute "print" for module name.  Do let me know if it works for you!

Regards,

Michael

---

### Post by clevershark on 2006-09-22
Maybe I'm missing something here, but after satisfying all dependencies (even docbook) when I run autogen.sh from the 5.0.1 CVS snapshot the ./configure step seems borked. This is the message I get:

configure: error: cannot find install-sh or install.sh in scripts ./scripts

Is anyone else having a problem here?

---

### Post by mschievano on 2006-10-01
> **michaeljt said:**
> Substitute "print" for module name.  Do let me know if it works for you!

Regards,

Michael

same error for me:

```

Running ./configure --enable-maintainer-mode --enable-compile-warnings ...
configure: error: cannot find install-sh or install.sh in scripts ./scripts

```

---

### Post by johnlr on 2006-10-12
> **mschievano said:**
> same error for me:

```

Running ./configure --enable-maintainer-mode --enable-compile-warnings ...
configure: error: cannot find install-sh or install.sh in scripts ./scripts

```

check this
automake --version

Make sure it is at least 1.9

---

### Post by clownius on 2006-10-15
Add me to the list of people who cant get this printer to work.  tried the cannon drivers with no luck.  Ill have a go on the instructions here and yell if i get it working.

Ok im a newbie still and cant work out how to install(or even download) a cvs and help apreciated.

---

### Post by IbeeX on 2006-10-15
> **clownius said:**
> Add me to the list of people who cant get this printer to work.  tried the cannon drivers with no luck.  Ill have a go on the instructions here and yell if i get it working.
I managed to install latest tuneprint CVS but still I don't see PIXIMA 4200 driver

---

### Post by clownius on 2006-10-15
Finally got my printer working.  Stumbled accross this in the wiki [https://wiki.ubuntu.com/CanonPixmaIP4200]("https://wiki.ubuntu.com/CanonPixmaIP4200")
  My only gripe is its printing painfully slow at my end but i can live with that.

If u can cut and paste u can get this printer working.

Thanks goes out to Steven_B  who seems to have done the first guide i can find.

Edit:If anyone could try this and tell me if they get glacial print speeds as well as id love to speed my  printer up to useable speeds.

Thanks Clownius

---

### Post by johnlr on 2006-10-18
I built 5.1 from cvs. The testpage looks ok, but printing onto CD from gimp does not work.

With the ip4000 driver that came with edgy, i could print to the cd, but cyan/magenta were out of whack. The driver I built just flashes the "paper out" led until I take out the CD tray. Then it prints the CD label onto paper. :-? cyan/magenta are still buggered on the paper too, but they work fine for the test page.

---

### Post by johnlr on 2006-10-20
If I set the printer to "Canon PIXMA 4000" in gimp, I can select "CD tray" as the media source. If I then switch to "Canon PIXMA 4200" that option goes away. :-?

---

### Post by dberg on 2006-10-22
> Finally got my printer working. Stumbled accross this in the wiki [https://wiki.ubuntu.com/CanonPixmaIP4200](https://wiki.ubuntu.com/CanonPixmaIP4200)
My only gripe is its printing painfully slow at my end but i can live with that.

If u can cut and paste u can get this printer working.

Thanks goes out to Steven_B who seems to have done the first guide i can find.

Edit:If anyone could try this and tell me if they get glacial print speeds as well as id love to speed my printer up to useable speeds.

Thanks Clownius

I used this and everything worked great! My print speeds are about the same as I have using this printer with Windows. Thanks for the link.

---

### Post by ramjet_1953 on 2006-10-23
if you go to the following site, the drivers are available in most languages. 

[http://software.canon-europe.com/](http://software.canon-europe.com/)

Roger

---

### Post by johnlr on 2006-10-24
> **dberg said:**
> I used this and everything worked great! My print speeds are about the same as I have using this printer with Windows. Thanks for the link.

Does this driver allow you to print on CDR?

---

### Post by dutchmega on 2006-11-06
Ubuntu Edgy here.

I tried to compile the Gutenprint CVS but I'm getting the following error during make:

genppd.c:78:25: error: cups/raster.h: No such file or directory

And indeed, it's nowhere near my computer :P (it also doesn't seem to be in the latest tar)

---

### Post by IbeeX on 2006-11-07
Hi I am also unable to compile gutenprint on edgy from cvs. Anybody managed to do this?

---

### Post by Cimmo on 2006-11-20
Guys enjoy these packages that works for my ip4200!!!
[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/)

The only thing is I've added the printer only via web interface, except this all is ok, and print is very good.

I think also 64 bit users have to wait for gutenprint 5.1.0 with ip4200 support
> The main driver is bjfilter* or cif* contained in bjfilter-2.x package. Cups reads ppd file in pstocanonbj package and calls pstocanonbj. The pstocanonbj calls bjfilter*. The bjfilter* needs libcnbj-2.x which is a proprietary library. The libcnbj-2.x does not work on platform other than i386, so it is impossible to suppoet ia64 and amd64.

---

### Post by IbeeX on 2006-12-08
hi I finally managed to install gutenprint driver from CVS and it 
works :) !!

---

### Post by Shelnutt2 on 2006-12-11
I've followed [this]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200") wiki guide. I used my laptop running 32 bit Ubuntu to convert the rpm's to .deb. Tehn used the --force-architecture option to install. The driver showed up and I installed/added my printer. But all is not good. It doesn't print.  It just sits here. I don't get any error messages. I'm not sure what to do. Anyone have any ideas?

Does the CVS work with ubuntu 64bit?

(I'm running Edgy)

---

### Post by Cimmo on 2006-12-11
> **Shelnutt2 said:**
> I've followed [this]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200") wiki guide. I used my laptop running 32 bit Ubuntu to convert the rpm's to .deb. Tehn used the --force-architecture option to install. The driver showed up and I installed/added my printer. But all is not good. It doesn't print.  It just sits here. I don't get any error messages. I'm not sure what to do. Anyone have any ideas?

Does the CVS work with ubuntu 64bit?

(I'm running Edgy)

Shelnutt I have posted just the solution with deb files created for Ubuntu... read and follow!

---

### Post by Shelnutt2 on 2006-12-11
> **Cimmo said:**
> Shelnutt I have posted just the solution with deb files created for Ubuntu... read and follow!

I followed your instructions, but it says it can not find the packages. I'm enabled all repositories and added yours. Any reason why it can't find your package? Maybe because I'm running 64 bit? (That always seems to be the problem)

---

### Post by Cimmo on 2006-12-11
> **Shelnutt2 said:**
> I followed your instructions, but it says it can not find the packages. I'm enabled all repositories and added yours. Any reason why it can't find your package? Maybe because I'm running 64 bit? (That always seems to be the problem)

for sure.
Only gutenprint 5.1.0 svn works for 64 bit, other packages based on Canon driver nope... sorry.
But I've written also this in my post ;)

---

### Post by IbeeX on 2006-12-12
> **Shelnutt2 said:**
> I've followed [this]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200") wiki guide. I used my laptop running 32 bit Ubuntu to convert the rpm's to .deb. Tehn used the --force-architecture option to install. The driver showed up and I installed/added my printer. But all is not good. It doesn't print.  It just sits here. I don't get any error messages. I'm not sure what to do. Anyone have any ideas?

Does the CVS work with ubuntu 64bit?

(I'm running Edgy)

Yes :) mine is also amd64

---

### Post by dbbolton on 2006-12-12
what about a xerox xk50cx ?

[http://www.ubuntuforums.org/showthread.php?t=317460](http://www.ubuntuforums.org/showthread.php?t=317460)

---

### Post by tom76 on 2007-01-01
If still current:

To install Canon IP4200 you need the Canon drivers: 

[http://software.canon-europe.com/software/0024302.asp?model=](http://software.canon-europe.com/software/0024302.asp?model=)

These are rpm files. If you're using Debian or similar you need the 'alien' program which you can download via the package manager ('Synaptic' in Debian, 'adept' in Ubuntu?). 
Untar the tar-file. 
You only need two of the created rpm-files, namely cnijfilter-common-2.60-1.i386.rpm and cnijfilter-ip4200-2.60-1.i386.rpm.
To convert these two files with 'alien', type the following command line in the console:

alien -c cnijfilter-common-2.60-1.i386.rpm cnijfilter-ip4200-2.60-1.i386.rpm

(The -c might be necessary to include scripts in the converting process.)

That should create two deb-files.
Install these two files by right-clicking them and choosing 'install' or something like that.
Type one more command in the console:

sudo /etc/init.d/cupsys restart

(This is necessary to restart the printer software again after the installation.)

Then configure the printer: go to 'utilities' or sth like that, and then 'printers'. Choose 'add' or similar. 
Choose the printer model Canon IP4200. 
Find the newly installed driver file canonip4200.ppd in the path: /usr/share/cups/model/canonip4200.ppd
Select it and finish the configuration. Set the printer as default. That should be all. 
(For what ever reasons the test page didn't seem to work with me, but the normal printing does.)

Compare: [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200)

---

### Post by tom76 on 2007-01-01
Please register your interest in future Canon drivers for Linux:

[http://www.canon-europe.com/Support/...ageID=312225#1](http://www.canon-europe.com/Support/...ageID=312225#1)

---

### Post by Cimmo on 2007-01-01
> **tom76 said:**
> Please register your interest in future Canon drivers for Linux:

[http://www.canon-europe.com/Support/...ageID=312225#1](http://www.canon-europe.com/Support/...ageID=312225#1)

url broken

---

### Post by tom76 on 2007-01-01
Sorry:
[http://www.canon-europe.com/Support/Software/Linux/registration.asp?ComponentID=312222&SourcePageID=312225](http://www.canon-europe.com/Support/Software/Linux/registration.asp?ComponentID=312222&SourcePageID=312225)

---

### Post by chriswakefield on 2007-01-26
I have the same printer. running amd X2 64 bit...Pure Debian, of course....;^)
I just hacked the Canon-BJC-4200-bjc600.ppd to be able to print a full page plus get 600 dpi.  Before all it would print was a half-size page.  Choose 600 dpi under printer options.
you can get it here:  [http://members.shaw.ca/c_wakefield/Canon-BJC-4200-bjc600.ppd](http://members.shaw.ca/c_wakefield/Canon-BJC-4200-bjc600.ppd)
Chris W.

---

### Post by agatha on 2007-03-03
> **Junkmaster357 said:**
> I'm using the Ubuntu AMD 64 bit.  I'm totally new to Ubuntu, and so far I love it.

I have a Canon PIXMA iP4200 Photo Printer, and I have absolutely no clue how to get it to work in Ubuntu.

Could someone please be kind enough to help me out here?
Instructions are at:-

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200)

Works well for me. NB this doesn't include drivers for the Easy-Print Toolbox, incldg CD printing

---

### Post by SigmundFreud on 2007-03-03
I finally managed to get my IP4200 working, and it's fast too. I followed the lead at [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/)  -- just install those packages. Then I manually added the printer using the CUPS webserver (127.0.0.1:631) -- you'll probably be asked for a name and password, in that case follow the instructions at [http://www.kdedevelopers.org/node/2117/](http://www.kdedevelopers.org/node/2117/)  (yes it's annoying). After that it all worked, I was surprised to say the least.

---

### Post by LostinSpacetime on 2007-06-11
Hi.. I also have this printer (ip4200) and I was positively surprised that Feisty Fawn was coming with a driver for it. I just have the problem that the colors don't match. I believe its using less or no margenta.. however red text is printed yellow. This is quite strange because the test print is perfect. Had anyone the same problem?

---

### Post by wompumudget on 2007-07-22
Hi all,

I am using Ubuntu Feisty Fawn, and have had bugs in the printing after following the instructions (minus the advanced features) given at:

[https://help.ubuntu.com/community/Ha...nonPixmaIP4200](https://help.ubuntu.com/community/Ha...nonPixmaIP4200)

The instructions worked, but now my printer isn't automatically noticed and I have to enter:

 sudo /etc/init.d/cupsys restart

after I restart or shut down my computer.  

Also, using openoffice writer, I printed a 5 page document and it wouldn't stop printing.  It printed all 5 pages and then repeated until out of paper.  Has anyone else had these problems?  I am curious to know when this Feisty Driver is planned on being released.  Very Excited! :) 

Also note that I am very green with Ubuntu.  Green friendly responses please.

My System:
Intel P3 733 MHz 
512 MB Rambus RAM
ATI Radion 9200

---

### Post by Cimmo on 2007-07-22
> **LostinSpacetime said:**
> Hi.. I also have this printer (ip4200) and I was positively surprised that Feisty Fawn was coming with a driver for it. I just have the problem that the colors don't match. I believe its using less or no margenta.. however red text is printed yellow. This is quite strange because the test print is perfect. Had anyone the same problem?

I can confirm this :(

---

