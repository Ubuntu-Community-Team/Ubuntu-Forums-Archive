---
title: "New HP ALL IN ONE PRINTER WILL NOT SCAN 14.04"
date: 2015-07-30
forum: Hardware
---

### Post by coljohnhannibalsmith on 2015-07-30
Hello,

I just purchased an HP Deskjet 1055 All-in-One J410 printer.  It will print flawlessly; but
it will not scan.  Neither Simple Scan nor XSane will work.  XSane gives the error message:

no devices available.

Apparently neither Simple Scan, nor XSane have detected the printer. Please see the attachment.

Thanks, Hannibal

---

### Post by howefield on 2015-07-31
Read this thread..  [http://ubuntuforums.org/showthread.php?t=1621081&page=3](http://ubuntuforums.org/showthread.php?t=1621081&page=3)

Caveat : It is an old one so be careful.

---

### Post by coljohnhannibalsmith on 2015-07-31
It didn't work.  The printer's still working though.

Thanks, Hannibal

---

### Post by tgalati4 on 2015-07-31
Open a terminal and describe what you see:

```
hp-toolbox
```

---

### Post by coljohnhannibalsmith on 2015-07-31
```
sophie@sophie-Inspiron-1545:~$ hp-toolbox
error: Unable to locate models.dat file

HP Linux Imaging and Printing System (ver. 0.0.0)
HP Device Manager ver. 15.0

Copyright (c) 2001-13 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

warning: Fax disabled.
warning: Fax disabled.
warning: Please install version 2.0+ of Reportlab for coverpage support.
error: Unable to locate models.dat file
error: Pixmap 'plus.png' not found!
error: Pixmap 'minus.png' not found!
error: dBus initialization error. Exiting.
error: Pixmap 'hp_logo.png' not found!
error: Pixmap 'fax2.png' not found!
error: Pixmap 'refresh1.png' not found!
error: Pixmap 'refresh.png' not found!
error: Pixmap 'list_add.png' not found!
error: Pixmap 'list_remove.png' not found!
error: Pixmap 'settings.png' not found!
error: Pixmap 'warning.png' not found!
error: Pixmap 'troubleshoot.png' not found!
error: Pixmap 'help.png' not found!
error: Pixmap 'quit.png' not found!
error: Pixmap 'battery.png' not found!
error: Pixmap 'cancel.png' not found!
error: Pixmap 'refresh.png' not found!
error: Pixmap 'busy.png' not found!
error: Pixmap 'busy.png' not found!
error: Pixmap 'print.png' not found!
error: Pixmap 'warning.png' not found!
error: Pixmap 'warning.png' not found!
error: Pixmap 'error.png' not found!
error: Pixmap 'ok.png' not found!
sophie@sophie-Inspiron-1545:~$ 

```

---

### Post by tgalati4 on 2015-08-02
Try reinstalling *hplip*.  Something is messed up.

```
sudo apt-get purge hplip
sudo apt-get install hplip
hp-toolbox
```

You should get a graphical dialog application that allows you to install printers, check ink levels, scan images, etc.

---

### Post by coljohnhannibalsmith on 2015-08-02
Done. When I launched hplip-toolbox, the splash screen displayed for about half a second,
then just disappeared. Neither simple-scan nor xsane could find a scanner.

I was also advised to run a shell script containing the following code:

#!/bin/bash

LINE=$(grep deskjet_1050_j410_series /usr/share/hplip/data/models/models.dat -n -A 60 | grep "io-mfp-mode=" | cut -d "-" -f 1)
sed -i.bak "$LINE s/io-mfp-mode=.*/io-mfp-mode=1/" /usr/share/hplip/data/models/models.dat
LINE=$(grep deskjet_1050_j410_series /usr/share/hplip/data/models/models.dat -n -A 60 | grep "scan-type=" | cut -d "-" -f 1)
sed -i.bak "$LINE s/scan-type=.*/scan-type=7/" /usr/share/hplip/data/models/models.dat

I also ran hp-check -t and discovered the following:

sophie@sophie-Inspiron-1545:~$ hp-check -t
error: Unable to locate models.dat file
Saving output in log file: /home/sophie/hp-check.log

HP Linux Imaging and Printing System (ver. 0.0.0)
Dependency/Version Check Utility ver. 15.1

Copyright (c) 2001-13 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Note: hp-check can be run in three modes:
1. Compile-time check mode (-c or --compile): Use this mode before compiling the
HPLIP supplied tarball (.tar.gz or .run) to determine if the proper dependencies
are installed to successfully compile HPLIP.                                    
2. Run-time check mode (-r or --run): Use this mode to determine if a distro    
supplied package (.deb, .rpm, etc) or an already built HPLIP supplied tarball   
has the proper dependencies installed to successfully run.                      
3. Both compile- and run-time check mode (-b or --both) (Default): This mode    
will check both of the above cases (both compile- and run-time dependencies).   

Check types:                                                                    
a. EXTERNALDEP - External Dependencies                                          
b. GENERALDEP - General Dependencies (required both at compile and run time)    
c. COMPILEDEP - Compile time Dependencies                                       
d. [All are run-time checks]                                                    
PYEXT SCANCONF QUEUES PERMISSION                                                

Status Types:
    OK
    MISSING       - Missing Dependency or Permission or Plug-in
    INCOMPAT      - Incompatible dependency-version or Plugin-version

Traceback (most recent call last):
  File "/usr/bin/hp-check", line 896, in <module>
    core.init()
  File "/usr/share/hplip/installer/core_install.py", line 372, in init
    self.distro_name = self.distros_index[self.distro]
KeyError: 0
sophie@sophie-Inspiron-1545:~$

So, this appears to be the problem:

[COLOR=#0000cd][I]error: Unable to locate models.dat file

[/I][/COLOR]There most certainly is a models.dat file; it's here:

[COLOR=#0000cd][/COLOR][COLOR=#0000cd][I]/usr/share/hplip/data/models/models.dat
                                                                                                                                                                                                                                                                                                    [/I][/COLOR]
Unfortunately, hplip toolbox can't find it. This looks like a path variable problem to me.[URL="http://ubuntuforums.org/newreply.php?p=10374397&noquote=1"]
[/URL]
Thanks, Hannibal

---

### Post by billy_harris2 on 2015-08-04
Been struggling with the same problem with a Photosmart 4425. I found  that, with the bundled version of HPLIP, the printer worked but the  scanner was not being recognised. Seems to be a permissions issue (as I could scan using  simplscan or hp-scan as root) but adding myself to the scanner group and  setting up a rule in /etc/sane.d/dll.conf did not help.

I ended up installing the latest hplip from the HP website - now I have a working scanner but no printer (and this time root can't print to it).

I'm thinking one option might be to revert to the bundled hplip (so the printer works), identify the device that corresponds to my scanner and change its owner to me - anyone know if that would work? I only have ine user account on the machine.

Billy.

---

### Post by coljohnhannibalsmith on 2015-08-04
Well, I tried running xsane and simple-scan as root and got a warning that that procedure
is EXTREMELY DANGEROUS. I have too much work in my dual-boot to hose it for experimental
purposes. Thanks; but no thanks.

Hannibal

---

### Post by oldfred on 2015-08-04
I have always downloaded the newest hplip from HP and it works. It also does its own updates which I do not like as much as I like Ubuntu repository. But never had troubles with updates either.

HP's newest On this website you can download the HPLIP software which supports 2,211 HP printers on nearly any Linux distribution available today.
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)
HP printers broken in Linux? Here's a fix. 
[http://www.dedoimedo.com/computers/linux-hp-printing.html](http://www.dedoimedo.com/computers/linux-hp-printing.html)

---

### Post by coljohnhannibalsmith on 2015-08-04
I already have the latest hplip installed.  I checked syslog and found the the following:

Aug  4 08:16:19 sophie-Inspiron-1545 xsane: io/hpmud/model.c 108: unable to open /etc/hp/hplip.conf: No such file or directory
Aug  4 08:16:19 sophie-Inspiron-1545 xsane: io/hpmud/model.c 532: no Deskjet_1050_J410_series attributes found in /data/models/models.dat
Aug  4 08:16:19 sophie-Inspiron-1545 xsane: io/hpmud/model.c 543: no Deskjet_1050_J410_series attributes found in /data/models/unreleased/unreleased.dat

Sure enough /etc/hp/hplip does not exist.  How can I force it to be created?

Thanks, Hannibal

---

### Post by coljohnhannibalsmith on 2015-08-04
In another thread it was recommended that I install hp-plugin. It couldn't be found.

Hannibal

---

### Post by coljohnhannibalsmith on 2015-08-04
Here's the info from models.dat that refers specifically to my All In One:

```
[deskjet_1050_j410_series]
align-type=-1
clean-type=1
color-cal-type=0
copy-type=0
embedded-server-type=0
fax-type=0
fw-download=False
icon=hp_deskjet_f4200.png
io-mfp-mode=1
io-mode=1
io-support=2
job-storage=0
linefeed-cal-type=0
model1=HP Deskjet 1050 J410 All-in-One Printer
model2=HP Deskjet 1051 All-in-One Printer
model3=HP Deskjet 1055 All-in-One Printer -J410e
model4=HP Deskjet 1056 All-in-One Printer -J410a
monitor-type=0
panel-check-type=1
pcard-type=0
plugin=0
plugin-reason=0
power-settings=0
pq-diag-type=0
r-type=1
r0-agent1-kind=3
r0-agent1-sku=61/61XL/61b
r0-agent1-type=1
r0-agent2-kind=3
r0-agent2-sku=61/61XL
r0-agent2-type=2
r10-agent1-kind=3
r10-agent1-sku=802/802XL/802b
r10-agent1-type=1
r10-agent2-kind=3
r10-agent2-sku=802/802XL
r10-agent2-type=2
r18-agent2-kind=3
r18-agent2-sku=93/95
r18-agent2-type=2
r18-agent3-kind=3
r18-agent3-sku=99
r18-agent3-type=3
r2-agent1-kind=3
r2-agent1-sku=61/61XL/61b
r2-agent1-type=1
r2-agent2-kind=3
r2-agent2-sku=61/61XL
r2-agent2-type=2
r4-agent1-kind=3
r4-agent1-sku=301/301XL/301b
r4-agent1-type=1
r4-agent2-kind=3
r4-agent2-sku=301/301XL
r4-agent2-type=2
r8-agent1-kind=3
r8-agent1-sku=122/122XL/122b
r8-agent1-type=1
r8-agent2-kind=3
r8-agent2-sku=122/122XL
r8-agent2-type=2
scan-src=1
scan-type=7
status-battery-check=0
status-dynamic-counters=1
status-type=2
support-released=True
support-subtype=219b2b
support-type=2
support-ver=3.10.6
tech-class=Pyramid
tech-subclass=NoAutoDuplex,NoCDDVD
tech-type=2
usb-pid=8911
usb-vid=3f0
wifi-config=0

```

Hannibal

---

### Post by tgalati4 on 2015-08-05
If it does't exist, then make one.  It seemed to work previously.  Unfortunately, there seems to be either a packaging problem with *hplip* or a CUPS installation problem (or both).  I would try a clean 14.04 installation on another machine and then try installing the printer.  Is the printer defined in the older version of *hplip*?

---

### Post by coljohnhannibalsmith on 2015-08-05
> **tgalati4 said:**
> If it does't exist, then make one.  It seemed to work previously.  Unfortunately, there seems to be either a packaging problem with *hplip* or a CUPS installation problem (or both).  I would try a clean 14.04 installation on another machine and then try installing the printer.  Is the printer defined in the older version of *hplip*?

I made an empty one and it didn't work. The scanner has never worked in 14.04. The printer is not
defined in the older version of hplip; and hplip-toolbox will not load. I'll try another machine.

Thanks, Hannibal

---

### Post by coljohnhannibalsmith on 2015-08-05
I did a fresh install on my other laptop and installed from Ubuntu NOT Flashback Compiz and
the scanner worked. During the install, I was asked to setup the printer, which I wasn't asked
to do in Flashback Compiz.  So, I uninstalled hplip and hplip toolbox and reinstalled hplip in
Ubuntu.  Unfortunately, I'm getting the same results that I've been having all along; and now
the printer doesn't work.

[COLOR=#ff0000][I]The new version of hplip keeps exiting during the Build and Install phase.
[/I][/COLOR]
Thanks, Hannibal

---

### Post by coljohnhannibalsmith on 2015-08-06
Bump.

BTW, I did get the printer working again; but the Ubuntu Test Page states that the driver version is 3.14.3.

The only difference between the 14.04 installation on my first machine and the second, was that on the 2nd
machine, I had the AIO printer connected at the time. At the time of my first installation, I did not own a 
printer.

---

### Post by coljohnhannibalsmith on 2015-08-07
Well, I decided to punt again. I copied the hplip.conf file from the second machine to the
first; and it appears that the scanner component of my AIO is working. The code is below:

```
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.15.7

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-3.15.7
html=/usr/share/doc/hplip-3.15.7
icon=/usr/share/applications
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv/hp
bin=/usr/bin

# Following values are determined at configure time and cannot be changed.
[configure]
network-build=yes
libusb01-build=no
pp-build=no
gui-build=yes
scanner-build=yes
fax-build=yes
dbus-build=yes
cups11-build=no
doc-build=yes
shadow-build=no
hpijs-install=no
foomatic-drv-install=no
foomatic-ppd-install=no
foomatic-rip-hplip-install=no
hpcups-install=yes
cups-drv-install=yes
cups-ppd-install=no
internal-tag=3.15.7
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
policy-kit=no
lite-build=no
udev_sysfs_rules=no
hpcups-only-build=no
hpijs-only-build=no
```

Please see the attachments.

What isn't working is that hplip 3.15.7 will not compile on the first machine, which is a DELL 1545
with a dual-core pentium, originally sold about 2009. The second machine is a DELL Inspiron 5520
with a quad-core I7. Could the failure to compile on my 1st machine be related to the pentium cores.
I think hplip should still compile as long as the distro is able to run on the pc; but I could be wrong.
Some opinions, or at least an educated guess please. The beauty of Linux is that it is supposed to
work on older machines. Is my 1st machine too old?

While the scanner now works, the cute little hp icon on the taskbar that lets me change my printer
settings doesn't appear without a successful build and install. Am I going to have to try and get source
code and modify it myself?

Thanks, Hannibal

---

### Post by tgalati4 on 2015-08-07
Compiling is tricky and really depends on how you set up your build environment.  I have not compiled *hplip*, so I can't comment directly, but typically you run a configure script first to verify that you have all of the pieces needed for a successful compile.  What were your compilation errors?

It's unlikely that CPU core type would cause a compilation failure.  I presume that you are running 64-bit linux on both systems.

It's not clear the benefit of going to a newer *hplip* if your printer is already supported in the 3.14.3 version.  Are the Agony Units worth it?

---

### Post by coljohnhannibalsmith on 2015-08-07
I'm using the .run file supplied by Source Forge. I'm not getting any compile errors; it's just exiting during the build and install phase, rather than completing the build and install. After it exits the old driver is still there; actually not any more; since, I copied a good hplip.conf from the 2nd system.

The scanner portion of my AIO and hplip toolbox are working correctly now. The only problem that remains is getting the first system to process the .run properly. However, this is important; since, I will undoubtedly have to upgrade hplip at some point in the future, especially if I have to buy a new printer.

Thanks, Hannibal

---

### Post by tgalati4 on 2015-08-08
Well, if the .run file is a script, you can go through line-by-line and run each command manually.  Eventually, you will see at what step it stops working.

---

### Post by coljohnhannibalsmith on 2015-08-08
> **tgalati4 said:**
> Well, if the .run file is a script, you can go through line-by-line and run each command manually.  Eventually, you will see at what step it stops working.

hplip-3.15.7.run is 22MB and took more than 10 minutes to completely load. Is it even possible to run a script this big by hand?

Thanks, Hannibal

---

### Post by tgalati4 on 2015-08-09
If it is a text file, then you can read it.  If it is a binary file, then it may be a zipped (compressed) file and executable only.  I have not tried to install a newer version of *hplip*, but obviously you are having problems with it and your configuration.

```
file hplip-3.15.7.run
```

---

### Post by coljohnhannibalsmith on 2015-08-10
sophie@sophie-Inspiron-1545:~$ file '/home/sophie/Downloads/hplip-3.15.7.run' 
/home/sophie/Downloads/hplip-3.15.7.run: data
sophie@sophie-Inspiron-1545:~$

---

### Post by tgalati4 on 2015-08-10
Have you tried:

```
sudo +x /home/sophie/Downloads/hplip-3.15.7.run
```

That makes it executable.  Files are not executable by default (as a security precaution).

Now change directories and run it.

```
cd /home/sophie/Downloads
./hplip-3.15.7.run
```

Don't forget the dot.

---

### Post by coljohnhannibalsmith on 2015-08-11
I got some useful output this time:

```
aries... yes
checking dynamic linker characteristics... (cached) GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for pthread_create in -lpthread... yes
checking for pow in -lm... yes
checking for jpeg_set_defaults in -ljpeg... yes
checking for dlopen in -ldl... yes
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking jpeglib.h usability... yes
checking jpeglib.h presence... yes
checking for jpeglib.h... yes
checking whether byte ordering is bigendian... no
checking for uint32_t... yes
checking "for platform-dependencies"... "using Default platform.h"
checking for documentation build... yes
checking for hpijs only build... no
checking for lite build... no
checking for hpcups only build... no
checking for hpijs install... no
checking for hpcups install... yes
checking for new hpcups install... no
checking for network build... yes
checking for parallel port build... no
checking for scanner build... yes
checking for gui build... yes
checking for fax build... yes
checking for dbus build... yes
checking for cups 1.1.x build... no
checking for udev sysfs enable rules... no
checking for shadow build... no
checking for libusb-0.1 build... no
checking for foomatic ppd install... no
checking for foomatic drv install... no
checking for cups drv install... yes
checking for cups ppd install... no
checking for foomatic-rip-hplip install... no
checking for qt4... yes
checking for qt3... no
checking for policykit... no
checking for host machine platform... x86_64
checking for CRYPTO_free in -lcrypto... checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking whether the C++ compiler works... yes
checking for C++ compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking how to print strings... printf
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking how to convert x86_64-unknown-linux-gnu file names to x86_64-unknown-linux-gnu format... func_convert_file_noop
checking how to convert x86_64-unknown-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for mt... mt
checking if mt is a manifest tool... no
checking how to run the C preprocessor... gcc -E
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
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking how to run the C++ preprocessor... g++ -E
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... (cached) GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for pthread_create in -lpthread... yes
checking for pow in -lm... yes
checking for jpeg_set_defaults in -ljpeg... yes
checking for dlopen in -ldl... yes
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking jpeglib.h usability... yes
checking jpeglib.h presence... yes
checking for jpeglib.h... yes
checking whether byte ordering is bigendian... no
checking for uint32_t... yes
checking "for platform-dependencies"... "using Default platform.h"
checking for documentation build... yes
checking for hpijs only build... no
checking for lite build... no
checking for hpcups only build... no
checking for hpijs install... no
checking for hpcups install... yes
checking for new hpcups install... no
checking for network build... yes
checking for parallel port build... no
checking for scanner build... yes
checking for gui build... yes
checking for fax build... yes
checking for dbus build... yes
checking for cups 1.1.x build... no
checking for udev sysfs enable rules... no
checking for shadow build... no
checking for libusb-0.1 build... no
checking for foomatic ppd install... no
checking for foomatic drv install... no
checking for cups drv install... yes
checking for cups ppd install... no
checking for foomatic-rip-hplip install... no
checking for qt4... yes
checking for qt3... no
checking for policykit... no
checking for host machine platform... x86_64
checking for CRYPTO_free in -lcrypto... yes
checking for snmp_timeout in -lnetsnmp... yes
checking net-snmp/net-snmp-config.h usability... yes
checking net-snmp/net-snmp-config.h presence... yes
checking for net-snmp/net-snmp-config.h... yes
checking for cupsDoFileRequest in -lcups... yes
checking cups/cups.h usability... checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking whether the C++ compiler works... yes
checking for C++ compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking how to print strings... printf
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking how to convert x86_64-unknown-linux-gnu file names to x86_64-unknown-linux-gnu format... func_convert_file_noop
checking how to convert x86_64-unknown-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for mt... mt
checking if mt is a manifest tool... no
checking how to run the C preprocessor... gcc -E
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
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking how to run the C++ preprocessor... g++ -E
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... (cached) GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for pthread_create in -lpthread... yes
checking for pow in -lm... yes
checking for jpeg_set_defaults in -ljpeg... yes
checking for dlopen in -ldl... yes
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking jpeglib.h usability... yes
checking jpeglib.h presence... yes
checking for jpeglib.h... yes
checking whether byte ordering is bigendian... no
checking for uint32_t... yes
checking "for platform-dependencies"... "using Default platform.h"
checking for documentation build... yes
checking for hpijs only build... no
checking for lite build... no
checking for hpcups only build... no
checking for hpijs install... no
checking for hpcups install... yes
checking for new hpcups install... no
checking for network build... yes
checking for parallel port build... no
checking for scanner build... yes
checking for gui build... yes
checking for fax build... yes
checking for dbus build... yes
checking for cups 1.1.x build... no
checking for udev sysfs enable rules... no
checking for shadow build... no
checking for libusb-0.1 build... no
checking for foomatic ppd install... no
checking for foomatic drv install... no
checking for cups drv install... yes
checking for cups ppd install... no
checking for foomatic-rip-hplip install... no
checking for qt4... yes
checking for qt3... no
checking for policykit... no
checking for host machine platform... x86_64
checking for CRYPTO_free in -lcrypto... yes
checking for snmp_timeout in -lnetsnmp... yes
checking net-snmp/net-snmp-config.h usability... yes
checking net-snmp/net-snmp-config.h presence... yes
checking for net-snmp/net-snmp-config.h... yes
checking for cupsDoFileRequest in -lcups... yes
checking cups/cups.h usability... yes
checking cups/cups.h presence... yes
checking for cups/cups.h... yes
checking for libusb_init in -lusb-1.0... yes
checking libusb-1.0/libusb.h usability... yes
checking libusb-1.0/libusb.h presence... yes
checking for libusb-1.0/libusb.h... yes
checking for a Python interpreter with version >= 2.2... python
checking for python... /usr/bin/python
checking for python version... 2.7
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.7/dist-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.7/dist-packages
checking for path to Python.h... "using /usr/include/python2.7 ....  python2.7/Python.h"
checking python2.7/Python.h usability... no
checking python2.7/Python.h presence... no
checking for python2.7/Python.h... no
checking python2.7mu/Python.h usability... no
checking python2.7mu/Python.h presence... no
checking for python2.7mu/Python.h... no
checking python2.7m/Python.h usability... checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking whether the C++ compiler works... yes
checking for C++ compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking how to print strings... printf
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking how to convert x86_64-unknown-linux-gnu file names to x86_64-unknown-linux-gnu format... func_convert_file_noop
checking how to convert x86_64-unknown-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for mt... mt
checking if mt is a manifest tool... no
checking how to run the C preprocessor... gcc -E
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
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking how to run the C++ preprocessor... g++ -E
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... (cached) GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for pthread_create in -lpthread... yes
checking for pow in -lm... yes
checking for jpeg_set_defaults in -ljpeg... yes
checking for dlopen in -ldl... yes
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking jpeglib.h usability... yes
checking jpeglib.h presence... yes
checking for jpeglib.h... yes
checking whether byte ordering is bigendian... no
checking for uint32_t... yes
checking "for platform-dependencies"... "using Default platform.h"
checking for documentation build... yes
checking for hpijs only build... no
checking for lite build... no
checking for hpcups only build... no
checking for hpijs install... no
checking for hpcups install... yes
checking for new hpcups install... no
checking for network build... yes
checking for parallel port build... no
checking for scanner build... yes
checking for gui build... yes
checking for fax build... yes
checking for dbus build... yes
checking for cups 1.1.x build... no
checking for udev sysfs enable rules... no
checking for shadow build... no
checking for libusb-0.1 build... no
checking for foomatic ppd install... no
checking for foomatic drv install... no
checking for cups drv install... yes
checking for cups ppd install... no
checking for foomatic-rip-hplip install... no
checking for qt4... yes
checking for qt3... no
checking for policykit... no
checking for host machine platform... x86_64
checking for CRYPTO_free in -lcrypto... yes
checking for snmp_timeout in -lnetsnmp... yes
checking net-snmp/net-snmp-config.h usability... yes
checking net-snmp/net-snmp-config.h presence... yes
checking for net-snmp/net-snmp-config.h... yes
checking for cupsDoFileRequest in -lcups... yes
checking cups/cups.h usability... yes
checking cups/cups.h presence... yes
checking for cups/cups.h... yes
checking for libusb_init in -lusb-1.0... yes
checking libusb-1.0/libusb.h usability... yes
checking libusb-1.0/libusb.h presence... yes
checking for libusb-1.0/libusb.h... yes
checking for a Python interpreter with version >= 2.2... python
checking for python... /usr/bin/python
checking for python version... 2.7
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.7/dist-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.7/dist-packages
checking for path to Python.h... "using /usr/include/python2.7 ....  python2.7/Python.h"
checking python2.7/Python.h usability... no
checking python2.7/Python.h presence... no
checking for python2.7/Python.h... no
checking python2.7mu/Python.h usability... no
checking python2.7mu/Python.h presence... no
checking for python2.7mu/Python.h... no
checking python2.7m/Python.h usability... no
checking python2.7m/Python.h presence... no
checking for python2.7m/Python.h... no
configure: error: cannot find python-devel support

sophie@sophie-Inspiron-1545:~/Downloads$ 

```

It looks like I might be missing a package; but [COLOR=#0000ff]*python-devel support *[/COLOR]doesn't tell me enough.

Thanks, Hannibal

---

### Post by coljohnhannibalsmith on 2015-08-11
Well, I checked synaptic for all packages found by using "python2.7" as a search term; and indeed there was one missing [COLOR=#0000ff]*"libpython2.7-dev."*[/COLOR] Installing this package made all the difference. Apparently this package does not get installed during the Ubuntu install from a Live-CD, unless there is a printer attached at the time of the Ubuntu install. I did not own a printer at the time. All is now well with hplip and 14.04.

Thanks, All:p

Hannibal

---

