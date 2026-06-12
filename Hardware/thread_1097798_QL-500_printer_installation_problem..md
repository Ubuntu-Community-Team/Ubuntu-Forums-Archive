---
title: "QL-500 printer installation problem."
date: 2009-03-16
forum: Hardware
---

### Post by Andre-D on 2009-03-16
I tried to install this driver: 
[http://www.diku.dk/hjemmesider/ansatte/panic/P-touch/]("http://www.diku.dk/hjemmesider/ansatte/panic/P-touch/")

The problem is that I still cannot select this printer-driver when installing, nor do I have a .PPD file.

I do not know if the process went well, but it seems so to me.

```

andre@LokeU:~/ptouch-driver-1.3$ ./configure 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for cupsParseOptions in -lcups... yes
checking for cupsRasterReadHeader in -lcupsimage... yes
checking for lrint in -lm... yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking cups/cups.h usability... yes
checking cups/cups.h presence... yes
checking for cups/cups.h... yes
checking cups/raster.h usability... yes
checking cups/raster.h presence... yes
checking for cups/raster.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking for an ANSI C-conforming const... yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for inline... inline
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking return type of signal handlers... void
checking for memset... yes
checking for strcasecmp... yes
checking for strstr... yes
checking for strtol... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: WARNING:  Makefile.in seems to ignore the --datarootdir setting
config.status: creating ptouch-driver.spec
config.status: creating ptouch-driver-foomatic.spec
config.status: creating config.h
config.status: executing depfiles commands



andre@LokeU:~/ptouch-driver-1.3$ sudo make
make  all-am
make[1]: Entering directory `/home/andre/ptouch-driver-1.3'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/andre/ptouch-driver-1.3'



andre@LokeU:~/ptouch-driver-1.3$ sudo make install
make[1]: Entering directory `/home/andre/ptouch-driver-1.3'
test -z "/usr/local/lib/cups/filter" || /bin/mkdir -p "/usr/local/lib/cups/filter"
  /usr/bin/install -c 'rastertoptch' '/usr/local/lib/cups/filter/rastertoptch'
test -z "/usr/local/share/foomatic/db/source" || /bin/mkdir -p "/usr/local/share/foomatic/db/source"
 /bin/bash /home/andre/ptouch-driver-1.3/install-sh -c -m 644 'driver/ptouch.xml' '/usr/local/share/foomatic/db/source/driver/ptouch.xml'
 /bin/bash /home/andre/ptouch-driver-1.3/install-sh -c -m 644 'printer/Brother-QL-500.xml' '/usr/local/share/foomatic/db/source/printer/Brother-QL-500.xml'
 /bin/bash /home/andre/ptouch-driver-1.3/install-sh -c -m 644 'printer/Brother-QL-550.xml' '/usr/local/share/foomatic/db/source/printer/Brother-QL-550.xml'
 /bin/bash /home/andre/ptouch-driver-1.3/install-sh -c -m 644 'printer/Brother-QL-650TD.xml' '/usr/local/share/foomatic/db/source/printer/Brother-QL-650TD.xml'
 /bin/bash /home/andre/ptouch-driver-1.3/install-sh -c -m 644 'printer/Brother-PT-PC.xml' '/usr/local/share/foomatic/db/source/printer/Brother-PT-PC.xml'
 /bin/bash /home/andre/ptouch-driver-1.3/install-sh -c -m 644 'printer/Brother-PT-18R.xml' '/usr/local/share/foomatic/db/source/printer/Brother-PT-18R.xml'
 /bin/bash /home/andre/ptouch-driver-1.3/install-sh -c -m 644 'printer/Brother-PT-1500PC.xml' '/usr/local/share/foomatic/db/source/printer/Brother-PT-1500PC.xml'
 /bin/bash /home/andre/ptouch-driver-1.3/install-sh -c -m 644 'printer/Brother-PT-1950VP.xml' '/usr/local/share/foomatic/db/source/printer/Brother-PT-1950VP.xml'
 /bin/bash /home/andre/ptouch-driver-1.3/install-sh -c -m 644 'printer/Brother-PT-1950.xml' '/usr/local/share/foomatic/db/source/printer/Brother-PT-1950.xml'
 /bin/bash /home/andre/ptouch-driver-1.3/install-sh -c -m 644 'printer/Brother-PT-1960.xml' '/usr/local/share/foomatic/db/source/printer/Brother-PT-1960.xml'
 /bin/bash /home/andre/ptouch-driver-1.3/install-sh -c -m 644 'printer/Brother-PT-2300.xml' '/usr/local/share/foomatic/db/source/printer/Brother-PT-2300.xml'
 /bin/bash /home/andre/ptouch-driver-1.3/install-sh -c -m 644 'printer/Brother-PT-2420PC.xml' '/usr/local/share/foomatic/db/source/printer/Brother-PT-2420PC.xml'
 /bin/bash /home/andre/ptouch-driver-1.3/install-sh -c -m 644 'printer/Brother-PT-2450DX.xml' '/usr/local/share/foomatic/db/source/printer/Brother-PT-2450DX.xml'
 /bin/bash /home/andre/ptouch-driver-1.3/install-sh -c -m 644 'printer/Brother-PT-2500PC.xml' '/usr/local/share/foomatic/db/source/printer/Brother-PT-2500PC.xml'
 /bin/bash /home/andre/ptouch-driver-1.3/install-sh -c -m 644 'printer/Brother-PT-2600.xml' '/usr/local/share/foomatic/db/source/printer/Brother-PT-2600.xml'
 /bin/bash /home/andre/ptouch-driver-1.3/install-sh -c -m 644 'printer/Brother-PT-2610.xml' '/usr/local/share/foomatic/db/source/printer/Brother-PT-2610.xml'
 /bin/bash /home/andre/ptouch-driver-1.3/install-sh -c -m 644 'printer/Brother-PT-3600.xml' '/usr/local/share/foomatic/db/source/printer/Brother-PT-3600.xml'
 /bin/bash /home/andre/ptouch-driver-1.3/install-sh -c -m 644 'printer/Brother-PT-550A.xml' '/usr/local/share/foomatic/db/source/printer/Brother-PT-550A.xml'
 /bin/bash /home/andre/ptouch-driver-1.3/install-sh -c -m 644 'printer/Brother-PT-9200DX.xml' '/usr/local/share/foomatic/db/source/printer/Brother-PT-9200DX.xml'
 /bin/bash /home/andre/ptouch-driver-1.3/install-sh -c -m 644 'printer/Brother-PT-9200PC.xml' '/usr/local/share/foomatic/db/source/printer/Brother-PT-9200PC.xml'
 /bin/bash /home/andre/ptouch-driver-1.3/install-sh -c -m 644 'printer/Brother-PT-9400.xml' '/usr/local/share/foomatic/db/source/printer/Brother-PT-9400.xml'
 /bin/bash /home/andre/ptouch-driver-1.3/install-sh -c -m 644 'printer/Brother-PT-9500PC.xml' '/usr/local/share/foomatic/db/source/printer/Brother-PT-9500PC.xml'
 /bin/bash /home/andre/ptouch-driver-1.3/install-sh -c -m 644 'printer/Brother-PT-9600.xml' '/usr/local/share/foomatic/db/source/printer/Brother-PT-9600.xml'
 /bin/bash /home/andre/ptouch-driver-1.3/install-sh -c -m 644 'opt/Brother-Ptouch-AdvanceDistance.xml' '/usr/local/share/foomatic/db/source/opt/Brother-Ptouch-AdvanceDistance.xml'
 /bin/bash /home/andre/ptouch-driver-1.3/install-sh -c -m 644 'opt/Brother-Ptouch-AdvanceMedia.xml' '/usr/local/share/foomatic/db/source/opt/Brother-Ptouch-AdvanceMedia.xml'
 /bin/bash /home/andre/ptouch-driver-1.3/install-sh -c -m 644 'opt/Brother-Ptouch-Align.xml' '/usr/local/share/foomatic/db/source/opt/Brother-Ptouch-Align.xml'
 /bin/bash /home/andre/ptouch-driver-1.3/install-sh -c -m 644 'opt/Brother-Ptouch-BytesPerLine.xml' '/usr/local/share/foomatic/db/source/opt/Brother-Ptouch-BytesPerLine.xml'
 /bin/bash /home/andre/ptouch-driver-1.3/install-sh -c -m 644 'opt/Brother-Ptouch-ConcatPages.xml' '/usr/local/share/foomatic/db/source/opt/Brother-Ptouch-ConcatPages.xml'
 /bin/bash /home/andre/ptouch-driver-1.3/install-sh -c -m 644 'opt/Brother-Ptouch-CutMark.xml' '/usr/local/share/foomatic/db/source/opt/Brother-Ptouch-CutMark.xml'
 /bin/bash /home/andre/ptouch-driver-1.3/install-sh -c -m 644 'opt/Brother-Ptouch-CutMedia.xml' '/usr/local/share/foomatic/db/source/opt/Brother-Ptouch-CutMedia.xml'
 /bin/bash /home/andre/ptouch-driver-1.3/install-sh -c -m 644 'opt/Brother-Ptouch-HalfCut.xml' '/usr/local/share/foomatic/db/source/opt/Brother-Ptouch-HalfCut.xml'
 /bin/bash /home/andre/ptouch-driver-1.3/install-sh -c -m 644 'opt/Brother-Ptouch-SoftwareMirror.xml' '/usr/local/share/foomatic/db/source/opt/Brother-Ptouch-SoftwareMirror.xml'
 /bin/bash /home/andre/ptouch-driver-1.3/install-sh -c -m 644 'opt/Brother-Ptouch-LabelPreamble.xml' '/usr/local/share/foomatic/db/source/opt/Brother-Ptouch-LabelPreamble.xml'
 /bin/bash /home/andre/ptouch-driver-1.3/install-sh -c -m 644 'opt/Brother-Ptouch-MirrorPrint.xml' '/usr/local/share/foomatic/db/source/opt/Brother-Ptouch-MirrorPrint.xml'
 /bin/bash /home/andre/ptouch-driver-1.3/install-sh -c -m 644 'opt/Brother-Ptouch-NegativePrint.xml' '/usr/local/share/foomatic/db/source/opt/Brother-Ptouch-NegativePrint.xml'
 /bin/bash /home/andre/ptouch-driver-1.3/install-sh -c -m 644 'opt/Brother-Ptouch-PageSize.xml' '/usr/local/share/foomatic/db/source/opt/Brother-Ptouch-PageSize.xml'
 /bin/bash /home/andre/ptouch-driver-1.3/install-sh -c -m 644 'opt/Brother-Ptouch-PixelTransfer.xml' '/usr/local/share/foomatic/db/source/opt/Brother-Ptouch-PixelTransfer.xml'
 /bin/bash /home/andre/ptouch-driver-1.3/install-sh -c -m 644 'opt/Brother-Ptouch-PrintDensity.xml' '/usr/local/share/foomatic/db/source/opt/Brother-Ptouch-PrintDensity.xml'
 /bin/bash /home/andre/ptouch-driver-1.3/install-sh -c -m 644 'opt/Brother-Ptouch-PrintQuality.xml' '/usr/local/share/foomatic/db/source/opt/Brother-Ptouch-PrintQuality.xml'
 /bin/bash /home/andre/ptouch-driver-1.3/install-sh -c -m 644 'opt/Brother-Ptouch-Resolution.xml' '/usr/local/share/foomatic/db/source/opt/Brother-Ptouch-Resolution.xml'
 /bin/bash /home/andre/ptouch-driver-1.3/install-sh -c -m 644 'opt/Brother-Ptouch-RollFedMedia.xml' '/usr/local/share/foomatic/db/source/opt/Brother-Ptouch-RollFedMedia.xml'
 /bin/bash /home/andre/ptouch-driver-1.3/install-sh -c -m 644 'opt/Brother-Ptouch-TransferMode.xml' '/usr/local/share/foomatic/db/source/opt/Brother-Ptouch-TransferMode.xml'
make[1]: Leaving directory `/home/andre/ptouch-driver-1.3'
andre@LokeU:~/ptouch-driver-1.3$ 

```


Later I found information that suggested to do this: 
```
 sudo cp -r /usr/local/share/foomatic/* /usr/share/foomatic 
```

now the printer installs fine, but printing gives this error:
"/usr/lib/cups/filter/foomatic-rip failed"

---

### Post by noxbrox on 2009-04-03
Hi,

I have a problem with this printer too.

Did you find how to create a PPD file for this ?

For the moment I have this message : 
```
./foomatic-datafile -p Brother-QL-550
ERROR: foomatic-datafile: There is neither a custom PPD file nor the driver database entry contains sufficient data to build a PPD file.

```

I have the ptouch.xml and the Brother-QL-550.xml files in /usr/share/foomatic/ but I still have this problem.

---

### Post by Andre-D on 2009-04-04
no I'm just using a driver, not a PPD. the driver is attached to my bugreport. 
You should subscribe and comment it, so it will gain more attention.
you'll find it here:
[http://bugs.linux-foundation.org/show_bug.cgi?id=325](http://bugs.linux-foundation.org/show_bug.cgi?id=325)

---

### Post by Andre-D on 2009-04-19
and now the bug is closed, because it's not a foomatic bug.
Only one thing left to do - complain to Brother.
I purchased this printer/brand *because* of the Linux support.

---

