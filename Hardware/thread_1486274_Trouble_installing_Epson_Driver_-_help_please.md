---
title: "Trouble installing Epson Driver - help please"
date: 2010-05-17
forum: Hardware
---

### Post by _Smiler_ on 2010-05-17
Hey, sorry if this is the wrong part of the forum, I can't see a part where printer problems would fit...let me know if you want it moved!

So, my problem is: I have 10.04 and an Epson SX215. Using the advice given [here]("http://ubuntuforums.org/showthread.php?p=8511014"), I found SX100 Gutenburg driver using the Printing utility in System>Administration. This picks up the printer, but when printing a test page, it just shoots out paper, sometimes ruining it with loads of jibberish symbols. So I clicked a few more links on that thread and ended up [here]("http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do") where I downloaded the tar.gz file of the "Epson ME Office 510, Epson Stylus NX215/SX210/SX215/TX210/TX213/TX219 " under "Image Scan! for Linux & Photo Image Print System Lite".

I navigate to the folder and ```
./configure
``` and it ended with: ```
cups-config missing
``` So I downloaded "libcupsys2-dev" after which ./configure ended with ```
checking for GDK_IMLIB... configure: error: Package requirements (imlibgdk) were not met:

No package 'imlibgdk' found
```

Where do I go from here? I hope I've provided enough info (sorry if it's too much). I'm still a bit of a newbie!

Oh, and I Googled "imlibgdk" and I came [here]("http://hany.sk/~hany/RPM/pkgconfig%28imlibgdk%29.html") so I searched for pkgconfig in Synaptic which gave me libextutils-pkgconfig-perl. Might that help? I don't like installing random things willy nilly even if I uninstall when I realise they're not needed as it seems to me it still clogs the system.

Am I going about all this the right way? When it comes to Ubuntu, I seem to spend more time on Google and this forum :S

---

### Post by claw1219 on 2010-06-01
check this out [http://ubuntuforums.org/showthread.php?t=522253](http://ubuntuforums.org/showthread.php?t=522253) it worked when i was installing my nx 510

just type 
sudo apt-get install libgtk2.0-dev libgtkglext1-dev


btw you need to have libltdl3-dev installed. you can get it from the Hardy repositories.

I also highly recommend using checkinstall to install the package

---

### Post by _Smiler_ on 2010-06-01
Hey thanks for helping me. I've installed checkinstall, but when I "make" I get this: ```
make  all-recursive
make[1]: Entering directory `/home/toes/pipslite-1.4.0'
Making all in lib
make[2]: Entering directory `/home/toes/pipslite-1.4.0/lib'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/toes/pipslite-1.4.0/lib'
Making all in lib-l2
make[2]: Entering directory `/home/toes/pipslite-1.4.0/lib-l2'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/toes/pipslite-1.4.0/lib-l2'
Making all in src
make[2]: Entering directory `/home/toes/pipslite-1.4.0/src'
Making all in filter-l2
make[3]: Entering directory `/home/toes/pipslite-1.4.0/src/filter-l2'
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../src/filter-l2/magick    -DCUPS_FILTER_PATH=\"/usr/local/lib/cups/filter\" -I../../lib-l2 -I../../src/filter-l2/ -g -O2 -Wall -MT l2filter.o -MD -MP -MF .deps/l2filter.Tpo -c -o l2filter.o l2filter.c
l2filter.c:45:25: error: cups/raster.h: No such file or directory
l2filter.c:68: error: expected ‘)’ before ‘*’ token
l2filter.c:76: error: expected ‘)’ before ‘*’ token
l2filter.c: In function ‘main’:
l2filter.c:125: error: ‘cups_raster_t’ undeclared (first use in this function)
l2filter.c:125: error: (Each undeclared identifier is reported only once
l2filter.c:125: error: for each function it appears in.)
l2filter.c:125: error: ‘cups_ras’ undeclared (first use in this function)
l2filter.c:126: error: ‘cups_page_header_t’ undeclared (first use in this function)
l2filter.c:126: error: expected ‘;’ before ‘header’
l2filter.c:137: error: ‘header’ undeclared (first use in this function)
l2filter.c:188: warning: implicit declaration of function ‘cupsRasterOpen’
l2filter.c:188: error: ‘CUPS_RASTER_READ’ undeclared (first use in this function)
l2filter.c:201: warning: implicit declaration of function ‘cupsRasterReadHeader’
l2filter.c:204: warning: implicit declaration of function ‘convert_cups_to_jpeg_1st’
l2filter.c:228: warning: implicit declaration of function ‘resize_jpeg’
l2filter.c:252: warning: implicit declaration of function ‘cupsRasterClose’
l2filter.c: At top level:
l2filter.c:779: error: expected ‘)’ before ‘*’ token
l2filter.c:1202: error: expected ‘)’ before ‘*’ token
make[3]: *** [l2filter.o] Error 1
make[3]: Leaving directory `/home/toes/pipslite-1.4.0/src/filter-l2'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/toes/pipslite-1.4.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/toes/pipslite-1.4.0'
make: *** [all] Error 2

```

I can't make sense of any of this, if I spoke the language I'd soldier on myself but I'd really appreciate if you could make sense of it and tell me what it means? Thanks so much!

---

### Post by _Smiler_ on 2010-06-01
I've run ./configure again and noticed that everything looks fine except:```
config.status: WARNING:  po/Makefile.in.in seems to ignore the --datarootdir setting
```

---

### Post by _Smiler_ on 2010-06-03
Ha! I hadn't actually tried the gutenprint driver provided with the printer utility. It hadn't worked in 8.10, so I'd been using windows for printing. Then I upgraded to 10.04 and it didn't occur that the driver might have been fixed...anyway, thanks for helping me.

---

