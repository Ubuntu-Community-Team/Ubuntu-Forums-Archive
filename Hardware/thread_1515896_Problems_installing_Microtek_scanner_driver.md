---
title: "Problems installing Microtek scanner driver"
date: 2010-06-23
forum: Hardware
---

### Post by undrline on 2010-06-23
I have a Mirotek ScanMaker 3800.  While it's not listed as a supported scanner, [the notes]("http://www.sane-project.org/unsupported/microtek-scanmaker-3800.html") refer to another scanner, 3840, which uses the same chipset and is mostly supported.  So, I tried to follow the directions to get that installed: [http://www.ziplabel.com/sm3840/](http://www.ziplabel.com/sm3840/) Which, again, also mentioned that my scanner might be supported.

Here's what I did:

[LIST]
[*]I saved sm3840_patch**2** and sm3840_source**5**.tar.gz to ~/Downloads/microtek/sm3840/
[*]In the Terminal, I pasted ```
patch -p1 < sm3840_patch2
```It told me I needed to install "patch" which did from Synaptic, and tried again.
[*]I got the following errors:
[/LIST]
[INDENT]```
patching file sane-backends-1.0.15/backend/dll.conf
Hunk #1 FAILED at 46.
1 out of 1 hunk FAILED -- saving rejects to file sane-backends-1.0.15/backend/dll.conf.rej
patching file sane-backends-1.0.15/backend/Makefile.in
Hunk #1 FAILED at 150.
Hunk #2 FAILED at 394.
2 out of 2 hunks FAILED -- saving rejects to file sane-backends-1.0.15/backend/Makefile.in.rej
patching file sane-backends-1.0.15/configure
Hunk #1 FAILED at 25618.
1 out of 1 hunk FAILED -- saving rejects to file sane-backends-1.0.15/configure.rej
patching file sane-backends-1.0.15/configure.in
Hunk #1 FAILED at 299.
1 out of 1 hunk FAILED -- saving rejects to file sane-backends-1.0.15/configure.in.rej
patching file sane-backends-1.0.15/doc/Makefile.in
Hunk #1 FAILED at 52.
Hunk #2 FAILED at 103.
2 out of 2 hunks FAILED -- saving rejects to file sane-backends-1.0.15/doc/Makefile.in.rej
patching file sane-backends-1.0.15/doc/sane.man
Hunk #1 FAILED at 376.
Hunk #2 FAILED at 804.
2 out of 2 hunks FAILED -- saving rejects to file sane-backends-1.0.15/doc/sane.man.rej

```[/INDENT]
[LIST]
[*]I tried it again with sudo, and got the same errors.
[*]Not knowing whether I could continue in spite of the errors, I went ahead with the next step, and the tar extracted successfully.
[*]The last step, it kept telling me there was no such thing as configure.
[/LIST]
I really think this is the key to getting my hardware up and running.  Searching on the forums, there are three other times that someone has tried to install this scanner, but no one has found or tried this.  I also tried contacting the author Earle F. Philhower III ([EMAIL="earle@ziplabel.com"]earle@ziplabel.com[/EMAIL]), but I haven't received a response yet.

Can someone walk me through what I might be doing wrong?

---

### Post by dino99 on 2010-06-23
give it a try: sudo update-pciids && update-usbids

[http://diplodrivers.com/download-driver/MICROTEK/SCANMAKER%203800](http://diplodrivers.com/download-driver/MICROTEK/SCANMAKER%203800)

[http://www.google.com/search?as_q=ScanMaker%2B3800%2Bubuntu&hl=fr&tbs=lr%3Alang_1en&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=lang_en&cr=&as_ft=i&as_filetype=&as_qdr=y&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images](http://www.google.com/search?as_q=ScanMaker%2B3800%2Bubuntu&hl=fr&tbs=lr%3Alang_1en&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=lang_en&cr=&as_ft=i&as_filetype=&as_qdr=y&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images)

---

### Post by IcarusR on 2010-06-23
Page with instructions is old. Patch is written against sane-backends-1.0.15 & you probably have a later version installed.

You could try editing the patch file, changing all reference to 1.0.15 to your version.
Alternately you could down grade sane-backends to 1.0.15.

---

### Post by undrline on 2010-06-23
Thank you both for responding.

@dino99
I get this result:
```
sudo update-pciids && update-usbids
[sudo] password for redacted: 
Downloaded daily snapshot dated     2010-06-12 03:15:02
touch: cannot touch `/var/lib/usbutils/usb.ids': Permission denied
/var/lib/usbutils/usb.ids is read-only, exiting.

```Not sure what the links were for (unless you were saying stfw)?  The first has a broken download link.  The second, a google search, redirects either back to this thread, the manufacturer, or links that I've already mentioned researching. :confused:

@IcarusR
It hadn't occurred to me that the patch might have the version number hard-coded.  It did occur to me to downgrade, make the patch, then upgrade again.  I don't know how to downgrade, though.  It'll take me a while to follow up on your advice.

---

### Post by desertdog on 2010-06-24
[https://help.ubuntu.com/community/CheckIfScannerIsClone](https://help.ubuntu.com/community/CheckIfScannerIsClone)

This wiki explains how to download sane source code, edit a couple of lines of code, then build from source. This technique hopefully will get you scanning.

---

### Post by undrline on 2010-06-24
> **desertdog said:**
> [https://help.ubuntu.com/community/CheckIfScannerIsClone](https://help.ubuntu.com/community/CheckIfScannerIsClone)

This wiki explains how to download sane source code, edit a couple of lines of code, then build from source. This technique hopefully will get you scanning.

Wow.  That's the kind of thing I was looking for, but couldn't find.  "Clone" wasn't exactly one of the keywords I was using  :rolleyes:

Sunday, I should have some time to work on this.
I now have a range of options.  Thank you!

---

### Post by undrline on 2010-06-27
So, I tried the easy thing first.  I extracted a version 1.0.15 sane-backends to ~/sane-backends-1.0.15, ran the patch successfully, extracted the sm3840 successfully, and then tried to run the compilation.  It resulted in permission errors, so I tried it again with sudo, and got errors:

```
sudo sane-backends-1.0.15/configure && make clean && make && make install
[sudo] password for redacted: 
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... yes
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking whether gcc needs -traditional... no
checking for sane-config... /usr/bin/sane-config
checking for msgfmt... no
checking for xgettext... no
checking for msgmerge... no
checking for latex... no
checking for dvips... no
checking for makeindex... no
checking linker parameter to set runtime link path... -Wl,-rpath,
checking for AIX... no
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
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking for library containing strerror... none required
checking mach-o/dyld.h usability... no
checking mach-o/dyld.h presence... no
checking for mach-o/dyld.h... no
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for dlopen in -ldl... yes
checking for dlopen... yes
checking dl.h usability... no
checking dl.h presence... no
checking for dl.h... no
checking for sqrt in -lm... yes
checking for scsireq_enter in -lscsi... no
checking for cam_open_device in -lcam... no
checking for gethostbyaddr in -lnsl... yes
checking for socket in -lsocket... no
checking for syslog in -lsyslog... no
checking for jpeg_start_decompress in -ljpeg... yes
checking jconfig.h usability... yes
checking jconfig.h presence... yes
checking for jconfig.h... yes
checking for jpeglib - version >= 61 (6a)... yes
checking ieee1284.h usability... yes
checking ieee1284.h presence... yes
checking for ieee1284.h... yes
checking for libieee1284 >= 0.1.5... yes
checking whether to enable pthread support... no
checking for pkg-config... pkg-config
checking for gp_camera_init... yes
checking for sane_init in -lsane... yes
checking for ANSI C header files... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for unistd.h... (cached) yes
checking libc.h usability... no
checking libc.h presence... no
checking for libc.h... no
checking sys/dsreq.h usability... no
checking sys/dsreq.h presence... no
checking for sys/dsreq.h... no
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking sys/shm.h usability... yes
checking sys/shm.h presence... yes
checking for sys/shm.h... yes
checking sys/scanio.h usability... no
checking sys/scanio.h presence... no
checking for sys/scanio.h... no
checking scsi.h usability... no
checking scsi.h presence... no
checking for scsi.h... no
checking sys/scsi.h usability... no
checking sys/scsi.h presence... no
checking for sys/scsi.h... no
checking sys/scsicmd.h usability... no
checking sys/scsicmd.h presence... no
checking for sys/scsicmd.h... no
checking sys/scsiio.h usability... no
checking sys/scsiio.h presence... no
checking for sys/scsiio.h... no
checking bsd/dev/scsireg.h usability... no
checking bsd/dev/scsireg.h presence... no
checking for bsd/dev/scsireg.h... no
checking scsi/sg.h usability... yes
checking scsi/sg.h presence... yes
checking for scsi/sg.h... yes
checking /usr/src/linux/include/scsi/sg.h usability... no
checking /usr/src/linux/include/scsi/sg.h presence... no
checking for /usr/src/linux/include/scsi/sg.h... no
checking io/cam/cam.h usability... no
checking io/cam/cam.h presence... no
checking for io/cam/cam.h... no
checking camlib.h usability... no
checking camlib.h presence... no
checking for camlib.h... no
checking os2.h usability... no
checking os2.h presence... no
checking for os2.h... no
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking sys/io.h usability... yes
checking sys/io.h presence... yes
checking for sys/io.h... yes
checking gscdds.h usability... no
checking gscdds.h presence... no
checking for gscdds.h... no
checking sys/hw.h usability... no
checking sys/hw.h presence... no
checking for sys/hw.h... no
checking for sys/types.h... (cached) yes
checking sys/scsi/scsi.h usability... no
checking sys/scsi/scsi.h presence... no
checking for sys/scsi/scsi.h... no
checking sys/scsi/sgdefs.h usability... no
checking sys/scsi/sgdefs.h presence... no
checking for sys/scsi/sgdefs.h... no
checking sys/scsi/targets/scgio.h usability... no
checking sys/scsi/targets/scgio.h presence... no
checking for sys/scsi/targets/scgio.h... no
checking apollo/scsi.h usability... no
checking apollo/scsi.h presence... no
checking for apollo/scsi.h... no
checking sys/sdi_comm.h usability... no
checking sys/sdi_comm.h presence... no
checking for sys/sdi_comm.h... no
checking sys/passthrudef.h usability... no
checking sys/passthrudef.h presence... no
checking for sys/passthrudef.h... no
checking linux/ppdev.h usability... yes
checking linux/ppdev.h presence... yes
checking for linux/ppdev.h... yes
checking dev/ppbus/ppi.h usability... no
checking dev/ppbus/ppi.h presence... no
checking for dev/ppbus/ppi.h... no
checking machine/cpufunc.h usability... no
checking machine/cpufunc.h presence... no
checking for machine/cpufunc.h... no
checking usb.h usability... yes
checking usb.h presence... yes
checking for usb.h... yes
checking sys/bitypes.h usability... yes
checking sys/bitypes.h presence... yes
checking for sys/bitypes.h... yes
checking sys/sem.h usability... yes
checking sys/sem.h presence... yes
checking for sys/sem.h... yes
checking sys/poll.h usability... yes
checking sys/poll.h presence... yes
checking for sys/poll.h... yes
checking IOKit/cdb/IOSCSILib.h usability... no
checking IOKit/cdb/IOSCSILib.h presence... no
checking for IOKit/cdb/IOSCSILib.h... no
checking IOKit/scsi-commands/SCSICommandOperationCodes.h usability... no
checking IOKit/scsi-commands/SCSICommandOperationCodes.h presence... no
checking for IOKit/scsi-commands/SCSICommandOperationCodes.h... no
checking windows.h usability... no
checking windows.h presence... no
checking for windows.h... no
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking asm/types.h usability... yes
checking asm/types.h presence... yes
checking for asm/types.h... yes
checking for asm/io.h... no
checking resmgr.h usability... no
checking resmgr.h presence... no
checking for resmgr.h... no
checking return type of signal handlers... void
checking for size_t... yes
checking for pid_t... yes
checking for ssize_t... yes
checking for u_int8_t only in sys/bitypes.h... no, also in standard headers
checking for u_int8_t... yes
checking for u_int16_t... yes
checking for u_int32_t... yes
checking for u_char... yes
checking for u_int... yes
checking for u_long... yes
checking for long long support... yes
checking for socklen_t in <sys/socket.h>... yes
checking for union semun in <sys/sem.h>... no
checking for sg_header.target_status in <scsi/sg.h>... yes
checking for struct flock in fcntl.h... yes
checking for Linux ioctl defines... yes
checking whether byte ordering is bigendian... no
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for working alloca.h... yes
checking for alloca... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking for atexit... yes
checking for inet_addr... yes
checking for inet_aton... yes
checking for inet_ntoa... yes
checking for ioperm... yes
checking for i386_set_ioperm... no
checking for mkdir... yes
checking for scsireq_enter... no
checking for strftime... yes
checking for strstr... yes
checking for strtod... yes
checking for cfmakeraw... yes
checking for tcsendbreak... yes
checking for strcasecmp... yes
checking for strncasecmp... yes
checking for _portaccess... no
checking for getaddrinfo... yes
checking for getnameinfo... yes
checking for poll... yes
checking for setitimer... yes
checking for iopl... yes
checking for getenv... yes
checking for inet_ntop... yes
checking for inet_pton... yes
checking for isfdtype... yes
checking for sigprocmask... yes
checking for snprintf... yes
checking for strdup... yes
checking for strndup... yes
checking for strsep... yes
checking for usleep... yes
checking for vsyslog... yes
checking for usb_get_busses in -lusb... yes
checking whether to enable IPv6... yes
checking whether struct sockaddr_storage has an ss_family member... yes
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking for dlfcn.h... (cached) yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
*** disabling PINT backend (sys/scanio.h not found)
*** disabling pnm backend (not selected manually)
scsi buffersize: 131072
disabling translations (missing msgfmt, xgettext or msgmerge)
configure: creating ./config.status
config.status: creating Makefile
config.status: creating lib/Makefile
config.status: creating sanei/Makefile
config.status: creating frontend/Makefile
config.status: creating japi/Makefile
config.status: creating backend/Makefile
config.status: creating include/Makefile
config.status: creating doc/Makefile
config.status: creating po/Makefile
config.status: creating testsuite/Makefile
config.status: creating tools/Makefile
config.status: creating doc/doxygen-sanei.conf
config.status: creating tools/sane-config
config.status: creating include/sane/config.h
config.status: include/sane/config.h is unchanged
-> Variables used for compilation/linking:
CPPFLAGS=" -DPATH_SANE_CONFIG_DIR=$(configdir) -DPATH_SANE_DATA_DIR=$(datadir) -DV_MAJOR=1 -DV_MINOR=0 -I/usr/include/gphoto2 -I/usr/include/libexif "
CFLAGS="-g -O2 -W -Wall"
LDFLAGS=" "
LIBS="-lusb -lnsl -lm -ljpeg -lieee1284 -lgphoto2 -lgphoto2_port -lexif -lm -lusb"
-> Installation directories:
Configuration: /usr/local/etc
Libraries:     /usr/local/lib
Binaries:      /usr/local/bin and /usr/local/sbin
Manpages:      /usr/local/man
Documentation: 
-> Network parameters:
Build saned:   yes
IPv6 support:  yes
-> The following backends will be built:
abaton agfafocus apple artec as6e avision bh canon canon630u coolscan coolscan2 dc25 dmc epson fujitsu gt68xx hp leo matsushita microtek microtek2 mustek mustek_usb nec pie plustek plustek_pp ricoh s9036 sceptre sharp sp15c st400 tamarack test teco1 teco2 teco3 umax umax_pp umax1220u artec_eplus48u ma1509 ibm hp5400 u12 snapscan niash sm3840 dc210 dc240 canon_pp hpsj5s mustek_pp gphoto2 qcam v4l net sm3600 
*** WARNING: SANE is already installed (version 1.0.20). The old
*** installation is at /usr while SANE will now be installed
*** at /usr/local. It is recommended to uninstall the old SANE version
*** before installing the new one to avoid problems.
****************************************************************
* Please be sure to read file PROBLEMS in this directory       *
* BEFORE running any of the SANE applications.  Some devices   *
* may be damaged by inproper operation, so please do heed this *
* advice.                                                      *
****************************************************************
making clean in include
make[1]: Entering directory `/home/redacted/include'
make[1]: Nothing to be done for `clean'.
make[1]: Leaving directory `/home/redacted/include'
making clean in lib
make[1]: Entering directory `/home/redacted/lib'
rm -f *.o *.lo *.a 
rm -rf .libs
make[1]: Leaving directory `/home/redacted/lib'
making clean in sanei
make[1]: Entering directory `/home/redacted/sanei'
rm -f *.o *.lo *.a  test_wire
rm -rf .libs
make[1]: Leaving directory `/home/redacted/sanei'
making clean in backend
make[1]: Entering directory `/home/redacted/backend'
rm -f *.lo *.o *.la libsane.la dll-preload.c
find . -type l -name \*-s.c | xargs rm -f
rm -rf .libs
make[1]: Leaving directory `/home/redacted/backend'
making clean in frontend
make[1]: Entering directory `/home/redacted/frontend'
rm -f *.o tstbackend
rm -rf .libs
make[1]: Leaving directory `/home/redacted/frontend'
making clean in tools
make[1]: Entering directory `/home/redacted/tools'
rm -f *.lo *.o *.la
find . -type l -name \*-s.c | xargs rm -f
rm -rf .libs
make[1]: Leaving directory `/home/redacted/tools'
making clean in doc
make[1]: Entering directory `/home/redacted/doc'
rm -f *.toc *.aux *.log *.cp *.fn *.tp *.vr *.pg *.ky *.blg *.idx *.cb
rm -f *.ilg
make[1]: Leaving directory `/home/redacted/doc'
making clean in po
make[1]: Entering directory `/home/redacted/po'
rm -f *.mo
rm -f *.old
rm -f *.pot
make[1]: Leaving directory `/home/redacted/po'
making all in include
make[1]: Entering directory `/home/redacted/include'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/redacted/include'
making all in lib
make[1]: Entering directory `/home/redacted/lib'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/redacted/lib'
making all in sanei
make[1]: Entering directory `/home/redacted/sanei'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/redacted/sanei'
making all in backend
make[1]: Entering directory `/home/redacted/backend'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/redacted/backend'
making all in frontend
make[1]: Entering directory `/home/redacted/frontend'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/redacted/frontend'
making all in tools
make[1]: Entering directory `/home/redacted/tools'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/redacted/tools'
making all in doc
make[1]: Entering directory `/home/redacted/doc'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/redacted/doc'
making all in po
make[1]: Entering directory `/home/redacted/po'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/redacted/po'
making install in include
make[1]: Entering directory `/home/redacted/include'
../sane-backends-1.0.15/mkinstalldirs /usr/local/include/sane
mkdir /usr/local/include/sane
mkdir: cannot create directory `/usr/local/include/sane': Permission denied
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/redacted/include'
make: *** [install-recursive] Error 1

```So, following the documentation that desertdog found for me, here is the scanner that was found:
```
found USB scanner (vendor=0x05da, product=0x30ce) at libusb:003:003

<device descriptor of 0x1d6b/0x0001 at 003:001>
bLength               18
bDescriptorType       1
bcdUSB                1.10
bDeviceClass          9
bDeviceSubClass       0
bDeviceProtocol       0
bMaxPacketSize0       64
idVendor              0x1D6B
idProduct             0x0001
bcdDevice             2.06
iManufacturer         3 ()
iProduct              2 ()
iSerialNumber         1 ()
bNumConfigurations    1
 <configuration 0>
 bLength              9
 bDescriptorType      2
 wTotalLength         25
 bNumInterfaces       1
 bConfigurationValue  1
 iConfiguration       0 ()
 bmAttributes         224 (Self-poweredRemote Wakeup)
 MaxPower             0 mA
  <interface 0>
   <altsetting 0>
   bLength            9
   bDescriptorType    4
   bInterfaceNumber   0
   bAlternateSetting  0
   bNumEndpoints      1
   bInterfaceClass    9
   bInterfaceSubClass 0
   bInterfaceProtocol 0
   iInterface         0 ()
    <endpoint 0>
    bLength           7
    bDescriptorType   5
    bEndpointAddress  0x81 (in 0x01)
    bmAttributes      3 (interrupt)
    wMaxPacketSize    2
    bInterval         255 ms
    bRefresh          0
    bSynchAddress     0
```I downloaded the sane dependencies and source code.  Then I got stuck.  In ~/sane-backends/backend/ none of the microtek files had a list of devices that could be edited to include my vendor/product id.

So, no luck so far.

---

### Post by desertdog on 2010-06-28
undrline:
For background information for others, you are trying to add support for the microtek scanmaker 3800. It is not currently supported, but it might be a clone of the microtek scanmaker 3840 or 4800, which are both supported by the sm3840 backend.

Complicating matters, there are several reports in the ubuntuforums (search microtek 3840 and microtek 4800) and elsewhere that the sm3840 backend only works on version 1.0.15, patched per instructions in [http://www.ziplabel.com/sm3840/](http://www.ziplabel.com/sm3840/). The sm3840 backend is apparently broken on later versions of sane.

So far you have downloaded and patched sane 1.0.15, and built from source.

I have a couple of suggestions and comments.

First, before you compile from source, make sure you have libusb-dev installed. This is essential. I would also install libsane-dev, although I am not certain that this is essential.

Secondly, I usually build sane as separate steps, ./configure, make, sudo make install. 

Third, for the ./configure step, i add the following flags --prefix=/usr --sysconfdir=/etc --localstatedir=/var.

So, I would run the following
$cd ~/sane-backends
$./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var
$make clean
$make
$sudo make install

Fourth, in the sm3840_source5.tar.gz, there are a bunch of files that need to be extracted and place in the ~/sanebackends/backend folder. Include in these is a file sm3840.c. Around line 549 of this code is where you will find the usb ids. You need to change one of these to match that of your scanner. Then run the build steps above.

When you are done building, 
$sane-find-scanner should find the scanner.
Then try
$scanimage -L 
and 
$sudo scanimage -L

If it is detected, then you are ready to start scanning. If only detected by sudo scanimage -L, then there is a permission problem, which there is a wiki at [https://help.ubuntu.com/community/Scanners](https://help.ubuntu.com/community/Scanners).

Good Luck!

---

### Post by desertdog on 2010-06-29
Just a quick update. The problems reported with the sm3840 backend all seem to be with version 1.0.19. The current version is 1.0.21, although I think ubuntu has 1.0.20 install by default.

In this post to the sane mailing list, the user says that 1.0.19 broke his 4800, but reverting to 1.0.18 fixed the problem. [http://lists.alioth.debian.org/pipermail/sane-devel/2008-April/021769.html](http://lists.alioth.debian.org/pipermail/sane-devel/2008-April/021769.html)

In a bug report, a developer states that the problem has been patched. [https://alioth.debian.org/tracker/?group_id=30186&atid=410366&func=detail&aid=310781](https://alioth.debian.org/tracker/?group_id=30186&atid=410366&func=detail&aid=310781).

So, I don't think you need to downgrade to 1.0.15 and patch. What you need to do is follow the instructions in [https://help.ubuntu.com/community/CheckIfScannerIsClone](https://help.ubuntu.com/community/CheckIfScannerIsClone).

Now there is one issue that you should clean up. You installed 1.0.15 without any modifiers to ./configure. This puts the sane libraries in /usr/local/lib/sane. Ubuntu comes with these in /usr/lib/sane. When you do ./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var, the files will will overwrite the files that came with Ubuntu, which is what you want. So you probably have sane installed in 2 places. To correct this you could 
$cd ~/sane-backends
$make uninstall
Then follow the directions in the clone check reference.
For reference, there is a readme file and a readme.linux in the ~/sane-backends folder.

Good luck.

---

### Post by undrline on 2010-06-29
> **desertdog said:**
> So, I don't think you need to downgrade to 1.0.15 and patch.
Great.


> **desertdog said:**
> Now there is one issue that you should clean up. You installed 1.0.15 without any modifiers to ./configure. This puts the sane libraries in /usr/local/lib/sane. Ubuntu comes with these in /usr/lib/sane. When you do ./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var, the files will will overwrite the files that came with Ubuntu, which is what you want. So you probably have sane installed in 2 places. To correct this you could 
$cd ~/sane-backends
$make uninstall

I had a feeling running through all this was creating junk.  The cleanup, however, didn't work :(
```
~/sane-backends$ make uninstall
make: *** No rule to make target `uninstall'.  Stop.

```

---

### Post by desertdog on 2010-06-29
Ok, so what I would do is delete the ~/sane-backends folder that contains the 1.0.15 version. 
Then follow the directions of [https://help.ubuntu.com/community/CheckIfScannerIsClone](https://help.ubuntu.com/community/CheckIfScannerIsClone)

Then, do $scanimage -V. This should return something like
scanimage (sane-backends) 1.0.22git; backend version 1.1.0.

If it does, then try to scan something. 

If it says that you are using 1.0.15, then run $sudo ldconfig. Then $cat /etc/ld.so.conf. Mine says:
include /etc/ld.so.conf.d/*.conf
include /usr/lib

You are going to want the second line to read like the one above. If it says: include /user/local/lib, you want to change it to /usr/lib, using a text editor as sudo.

---

### Post by undrline on 2010-06-30
> **desertdog said:**
> undrline:
For background information for others...

All correct.  Exactly what I'm trying to do.

> Fourth, in the sm3840_source5.tar.gz, there are a bunch of files that  need to be extracted and place in the ~/sanebackends/backend folder.  Include in these is a file sm3840.c. Around line 549 of this code is  where you will find the usb ids. You need to change one of these to  match that of your scanner. Then run the build steps above.
Copied files from sm3840_source5.tar.gz backend directory to the ~/sanebackends/backend/ directory, skipping those that were already existed.  Added these lines in the appropriate places to ~/sanebackends/backend/sm3840.c:
```
static SANE_Status
add_sm3800_device (SANE_String_Const devname)
{
  return add_sm_device (devname, "ScanMaker 3800");
}

``````
  sanei_usb_find_devices (0x05da, 0x30ce, add_sm3800_device);
```> 
First, before you compile from source, make sure you have libusb-dev  installed. This is essential. I would also install libsane-dev, although  I am not certain that this is essential.Both were already installed.

> So, I would run the following
$cd ~/sane-backends
$./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var
$make clean
$make
$sudo make install


When you are done building, 
$sane-find-scanner should find the scanner.
Then try
$scanimage -L 
and 
$sudo scanimage -L

If it is detected, then you are ready to start scanning.WTG, I got this far, and it was detected without sudo!
```
device `sm3840:libusb:003:002' is a Microtek ScanMaker 3800 flatbed scanner
```I then opened up XSANE, and got an error :mad:
```
Failed to open device `sm3840:libusb:003:002': Access to resource has been denied.
```I then opened up Simple Scan and it found it, but then trying to scan yeilds an error, unable to connect to scanner.

So, I need to read those links you posted where 3840 was mentioned elsewhere in the forum, as well as the scanners wiki.  I also need to follow the cleanup instructions.

$scanimage -V shows this right now:
```
scanimage (sane-backends) 1.0.22git; backend version 1.0.22
```Wait ... I just looked at the CheckIfScannerIsClone ... you've been getting it updated as we go along.  I skipped the step where I edit /etc/sane.d/sm3840.conf ... I'm going through the steps again now.

---

### Post by undrline on 2010-06-30
Hmm.  It appeared to work.  For the first time, I take an action on the machine, and the scanner responds.  There might be something wrong with the scanner, since the lamp appears to be stuck with grinding noises.  It'd be a shame to have gone through all of this for a broken scanner.  Scanning an image via "scanimage >image.pnm" only works with sudo, so I think there's a permissions issue.  I tried every single option on the [_SettingScannerPermissions_]("https://help.ubuntu.com/community/SettingScannerPermissions") page, and none of them change the "scanimage: open of device sm3840:libusb:003:017 failed: Access to resource has been denied" error from appearing (also via XSANE).

---

### Post by desertdog on 2010-06-30
If you hear grinding noises, you need to unplug the scanner. If you let those go on too long, it could damage the scanner. You could hook it up to a windows machine and make sure that it still works correctly.

Since your scanner is recognized by sudo scanimage -L, but does not scan correctly, it probably is not an exact copy of the sm3840. 

A couple of things come to mind to try. scanimage -T will give some debugging information. You could try scanimage with a couple of modifiers, like $scanimage --resolution 75 --mode Color >test.pnm

If you "hijacked" the sm3840, and it didn't work correctly, you could retry with the 4800. Maybe there are differences between the two of them.

If it turns out that your scanner is not a clone of one of the existing scanners, the next step is very advanced, and you will need to write to the sane-devel mailing list. 

They will want probably want you to send them a debugging output and to have you snoop the usbtraffic with the scanner attached to a windows box.

Debugging logs are generated by the following commands:
$export SANE_DEBUG_SM3840=255
$scanimage --resolution 100 --mode Color >100dpi-scan.pnm 2> logfile
    or 
$scanimage --mode Color --resolution 100 2>scan.log >scan.pnm

Unfortunately, the creator of the sm3840 backend is not very active on the sane mailing list.

---

### Post by undrline on 2010-06-30
I tried it on my company's Windows machine, and it works just fine.  So, I guess it is a problem with the setup.  ](*,)

> If you "hijacked" the sm3840, and it didn't work correctly, you could  retry with the 4800. Maybe there are differences between the two of  them.I thought the 4800 was hijacking the 3840 as well.  Maybe I'm not understanding the concept.

I guess I need to go to the "advanced" level.  Thanks for sticking with me on this.  I really appreciate it.

---

### Post by undrline on 2010-06-30
k, I've got the logs (attached) ... do I just send them to the mailing list email ([EMAIL="sane-devel@lists.alioth.debian.org"]sane-devel@lists.alioth.debian.org[/EMAIL])? do I say anything by way of introduction?

$export SANE_DEBUG_SM3840=255 didn't appear to do anything.  Is there a log I should be looking for related to that command?

---

### Post by desertdog on 2010-07-01
Hi,
The scanimage -T log looks like it ran okay. 

To get the other logs first type
$export SANE_DEBUG_SM3840=255
nothing will happen, then type 
$scanimage --resolution 150 --mode Color >150dpi-scan.pnm 2> logfile

(If scanner is still only recognized with sudo, then add sudo to the scanimage above).
Then look in folder that you are scanning in and there should be a file called logfile and an image called 150dpi-scan.pnm. You can check the image to see how it looks and look over the log file to see if it gets to a certain point and says there is some kind of problem.

Your usb snoop log doesn't look quite right. You could probably hold off on doing this.

I would email the sane-devel list and let them know you have a sm3800 scanner, that uses the same chip as other scanners supported by the sm3840 backend and you have modified the usb id in sm3840.c file. Tell them that your scanner is now recognized with scanimage -L (or sudo scanimage -L). Tell them whether there is a recognizable image produced, and describe funny scanner noises. If there is an acceptable image at a certain resolution or mode, that would be important to note.

You could compress and attach the log file. There is a size limit to attachment to that mailing list, so don't attach the image. Ask if anyone could look at your debug log and offer any suggestions.

---

### Post by undrline on 2010-07-06
It took me a little while, but I posted to the mailing list.  So far, no response to my post.

---

