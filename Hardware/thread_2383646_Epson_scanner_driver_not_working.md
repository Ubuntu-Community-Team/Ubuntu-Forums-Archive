---
title: "Epson scanner driver not working"
date: 2018-01-27
forum: Hardware
---

### Post by Zobeid on 2018-01-27
Running Ubuntu MATE 17.10 and trying to get an Epson Perfection V600 Photo scanner to work.  I did download the driver package from Epson, it seemed to install OK, but my system still says there is no scanner present.  I've tried different USB cables and ports, tried rebooting.  I tried digging up different versions of the Epson driver package, but it didn't make any difference.  I have "Image Scan" and "Image Scan! for Linux" and "Simple Scan" and "XSane Image scanning program", and none of them recognize the presence of a scanner.

Any suggestions what I should try next?

Would I get anywhere by calling Epson?

If I don't get this sorted out eventually, I am willing to buy a new scanner—a Canon, perhaps—if it's known to work without problems.

---

### Post by pqwoerituytrueiwoq on 2018-01-27
can you post the output of these commands?
[FONT=courier new]lsusb
scanimage -L
scanimage --help[/FONT]


edit: also do the last 2 with sudo

---

### Post by pdc on 2018-01-28
I think there have been a number of threads reporting issues with 17.10 and scanning; 

the next Ubuntu release is the 18.04; which is to be LTS; and the emphasis there is stability; in between, Ubuntu innovate and push boundaries with short-term releases; if you report the issues to Ubuntu as a bug; we hope whatever has changed in scanning can be resolved; earlier stable versions; eg 16.04 the LTS all seem fine with the Epson drivers

---

### Post by Zobeid on 2018-01-28
I got this…

```
zobeid@zobeid-desktop:~$ lsusb
Bus 004 Device 007: ID 0451:8140 Texas Instruments, Inc. 
Bus 004 Device 005: ID 2109:0812 VIA Labs, Inc. VL812 Hub
Bus 004 Device 006: ID 0451:8140 Texas Instruments, Inc. 
Bus 004 Device 004: ID 0451:8140 Texas Instruments, Inc. 
Bus 004 Device 003: ID 0451:8140 Texas Instruments, Inc. 
Bus 004 Device 002: ID 0525:3101 Netchip Technology, Inc. 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 010: ID 0451:ca01 Texas Instruments, Inc. 
Bus 003 Device 008: ID 0451:8142 Texas Instruments, Inc. TUSB8041 4-Port Hub
Bus 003 Device 006: ID 2109:2812 VIA Labs, Inc. VL812 Hub
Bus 003 Device 004: ID 5332:1400  
Bus 003 Device 011: ID 0451:ca01 Texas Instruments, Inc. 
Bus 003 Device 009: ID 0451:8142 Texas Instruments, Inc. TUSB8041 4-Port Hub
Bus 003 Device 015: ID feed:2260  
Bus 003 Device 016: ID 195d:6008 Itron Technology iONE 
Bus 003 Device 003: ID 0451:8142 Texas Instruments, Inc. TUSB8041 4-Port Hub
Bus 003 Device 002: ID 0451:8142 Texas Instruments, Inc. TUSB8041 4-Port Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0aa7 Intel Corp. 
Bus 001 Device 006: ID 04b8:013a Seiko Epson Corp. GT-X820 [Perfection V600 Photo]
Bus 001 Device 004: ID 04f9:0061 Brother Industries, Ltd 
Bus 001 Device 003: ID 1a40:0201 Terminus Technology Inc. FE 2.1 7-port Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```
zobeid@zobeid-desktop:~$ sudo scanimage -L
[bjnp] create_broadcast_socket: ERROR - bind socket to local address failed - Address already in use

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

```

```
zobeid@zobeid-desktop:~$ sudo scanimage --help
Usage: scanimage [OPTION]...

Start image acquisition on a scanner device and write image data to
standard output.

Parameters are separated by a blank from single-character options (e.g.
-d epson) and by a "=" from multi-character options (e.g. --device-name=epson).
-d, --device-name=DEVICE   use a given scanner device (e.g. hp:/dev/scanner)
    --format=pnm|tiff|png|jpeg  file format of output file
-i, --icc-profile=PROFILE  include this ICC profile into TIFF file
-L, --list-devices         show available scanner devices
-f, --formatted-device-list=FORMAT similar to -L, but the FORMAT of the output
                           can be specified: %d (device name), %v (vendor),
                           %m (model), %t (type), %i (index number), and
                           %n (newline)
-b, --batch[=FORMAT]       working in batch mode, FORMAT is `out%d.pnm' `out%d.tif'
                           `out%d.png' or `out%d.jpg' by default depending on --format
    --batch-start=#        page number to start naming files with
    --batch-count=#        how many pages to scan in batch mode
    --batch-increment=#    increase page number in filename by #
    --batch-double         increment page number by two, same as
                           --batch-increment=2
    --batch-print          print image filenames to stdout
    --batch-prompt         ask for pressing a key before scanning a page
    --accept-md5-only      only accept authorization requests using md5
-p, --progress             print progress messages
-n, --dont-scan            only set options, don't actually scan
-T, --test                 test backend thoroughly
-A, --all-options          list all available backend options
-h, --help                 display this help message and exit
-v, --verbose              give even more status messages
-B, --buffer-size=#        change input buffer size (in kB, default 32)
-V, --version              print version information
[bjnp] create_broadcast_socket: ERROR - bind socket to local address failed - Address already in use
scanimage: no SANE devices found

```

also…

```
zobeid@zobeid-desktop:~$ sudo sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

could not fetch string descriptor: Pipe error
could not fetch string descriptor: Pipe error
could not fetch string descriptor: Pipe error
could not fetch string descriptor: Pipe error
found USB scanner (vendor=0x04b8 [EPSON], product=0x013a [EPSON Scanner]) at libusb:001:006
could not fetch string descriptor: Pipe error
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

```

---

### Post by bjherbison on 2018-02-12
Any new information (other than wait for 18.4)?

I have a different model Epson and I'm getting the same symptoms. (Shows up in USB devices, sane-find-scanner finds it, but scanimage doesn't find it.)

---

### Post by rbmorse on 2018-02-12
See message #7 in this thread:

[https://ubuntuforums.org/showthread.php?t=2374868&highlight=Epson+4490](https://ubuntuforums.org/showthread.php?t=2374868&highlight=Epson+4490)

Didn't work for me, but others reported success with this.

---

### Post by ofde on 2018-05-08
I have contacted with Epson support and I explained this problem. First reply is I must install the driver. I explain again that the driver is installed but is not recognized by system. Second reply from Epson is them not do support to linux. We will consider it when buying the next scanner.

My system: Ubuntu 18.04
My scanner: Epson Perfection V200 Photo

---

### Post by ivo.kovacic.sk on 2018-05-08
Solution can be found here
[https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/1728012](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/1728012)
See post #25 - [TABLE]
[TR]
[TD][staedtler-przyborski (staedtler-przyborski)]("https://launchpad.net/~staedtler-przyborski") wrote on 2017-11-03:[/TD]
[TD="class: bug-comment-index"][#25]("https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/1728012/comments/25")[/TD]
[/TR]
[/TABLE]

[COLOR=#333333][FONT=monospace]Epson Iscan[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]a) 'sudo ln -sfr /usr/lib/sane/libsane-epkowa* /usr/lib/x86_64-linux-gnu/sane'
b) generate '/etc/udev/rules.d/79-udev-epson.rules'
content:
# chmod device EPSON group
ATTRS{manufacturer}=="EPSON", DRIVERS=="usb", SUBSYSTEMS=="usb", ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="*", MODE="0777"

I have used it for Epson V370 and it is working.
I consider it verified.
V Ubuntu 18.04 64 bit used and upgraded since 14.04, running on Asus X550C.[/FONT][/COLOR]

---

### Post by lrkwz on 2018-05-18
> **ivo.kovacic.sk said:**
> Solution can be found here
I have used it for Epson V370 and it is working.
I consider it verified.
V Ubuntu 18.04 64 bit used and upgraded since 14.04, running on Asus X550C.[/FONT][/COLOR]

Works for me as well:

Epson Perfection V330 Photo
Ubuntu 18.04 64 Bit, running on Dell Precision M4500

---

### Post by kngharv on 2018-06-29
You just saved my life.   Thank you so much!




> **ivo.kovacic.sk said:**
> Solution can be found here
[https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/1728012](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/1728012)
See post #25 - [TABLE]
[TR]
[TD][staedtler-przyborski (staedtler-przyborski)]("https://launchpad.net/~staedtler-przyborski") wrote on 2017-11-03:[/TD]
[TD="class: bug-comment-index"][#25]("https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/1728012/comments/25")[/TD]
[/TR]
[/TABLE]

[COLOR=#333333][FONT=monospace]Epson Iscan[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]a) 'sudo ln -sfr /usr/lib/sane/libsane-epkowa* /usr/lib/x86_64-linux-gnu/sane'
b) generate '/etc/udev/rules.d/79-udev-epson.rules'
content:
# chmod device EPSON group
ATTRS{manufacturer}=="EPSON", DRIVERS=="usb", SUBSYSTEMS=="usb", ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="*", MODE="0777"

I have used it for Epson V370 and it is working.
I consider it verified.
V Ubuntu 18.04 64 bit used and upgraded since 14.04, running on Asus X550C.[/FONT][/COLOR]

---

### Post by rjrich on 2018-07-15
> **ivo.kovacic.sk said:**
> Solution can be found here
[https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/1728012](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/1728012)
See post #25 - [TABLE]
[TR]
[TD][staedtler-przyborski (staedtler-przyborski)]("https://launchpad.net/~staedtler-przyborski") wrote on 2017-11-03:[/TD]
[TD="class: bug-comment-index"][#25]("https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/1728012/comments/25")[/TD]
[/TR]
[/TABLE]

[COLOR=#333333][FONT=monospace]Epson Iscan[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]a) 'sudo ln -sfr /usr/lib/sane/libsane-epkowa* /usr/lib/x86_64-linux-gnu/sane'
b) generate '/etc/udev/rules.d/79-udev-epson.rules'
content:
# chmod device EPSON group
ATTRS{manufacturer}=="EPSON", DRIVERS=="usb", SUBSYSTEMS=="usb", ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="*", MODE="0777"

I have used it for Epson V370 and it is working.
I consider it verified.
V Ubuntu 18.04 64 bit used and upgraded since 14.04, running on Asus X550C.[/FONT][/COLOR]
=====

Thank you very much indeed for this solution! I can confirm that it works with the Epson V600 Perfection Photoscanner and Linux Mint 19 64-bit LTS Xfce (based on Ubuntu 18.04 64-bit LTS).

---

### Post by kracheck on 2018-08-11
I have an old Epson XP-205 which I used for wireless scanning. Worked great in my home network under ubuntu 16.04 LTS. It doesn't work anymore with ubuntu 18.04 LTS.
Does the suggested solution also apply to network connected Epson printers with scan function  ?

---

### Post by kracheck on 2018-08-13
Tried it and doesn't seem to work. Solved it by installing CUPS and SANE on a raspberry pi and attaching it to the USB port of the printer. Now I'm able to scan wireless again.

---

### Post by dezavuisan on 2018-08-13
> **ivo.kovacic.sk said:**
> Solution can be found here
[https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/1728012](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/1728012)
See post #25 - [TABLE]
[TR]
[TD][staedtler-przyborski (staedtler-przyborski)]("https://launchpad.net/~staedtler-przyborski") wrote on 2017-11-03:[/TD]
[TD="class: bug-comment-index"][#25]("https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/1728012/comments/25")[/TD]
[/TR]
[/TABLE]

[COLOR=#333333][FONT=monospace]Epson Iscan[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]a) 'sudo ln -sfr /usr/lib/sane/libsane-epkowa* /usr/lib/x86_64-linux-gnu/sane'
b) generate '/etc/udev/rules.d/79-udev-epson.rules'
content:
# chmod device EPSON group
ATTRS{manufacturer}=="EPSON", DRIVERS=="usb", SUBSYSTEMS=="usb", ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="*", MODE="0777"

I have used it for Epson V370 and it is working.
I consider it verified.
V Ubuntu 18.04 64 bit used and upgraded since 14.04, running on Asus X550C.[/FONT][/COLOR]


New installation of Ubuntu 18.04, installed Epson drivers for Epson ET-3750 from for Ubuntu 18.04 Epson web site. Network scanner not recognized neither in Image Scan nor by [FONT=courier new]sudo scanimage -L[/FONT].
The above fix proposal does not help because:
[LIST=1]
[*]There is no [SIZE=2][FONT=courier new][COLOR=#333333]/usr/lib/sane[/COLOR][/FONT][/SIZE] directory - all [FONT=courier new][SIZE=2]libsane[/SIZE][/FONT] files are already in [FONT=courier new][SIZE=2]/usr/lib/x86_64-linux-gnu/sane[/SIZE][/FONT].
[*][FONT=courier new][SIZE=2][/SIZE][/FONT]There are no [FONT=courier new]libsane-epkowa*[/FONT] files, but there are [FONT=courier new]libsane-epson.so.1[/FONT], [FONT=courier new]libsane-epson2.so.1[/FONT] and [FONT=courier new]libsane-epsonds.so.1[/FONT] files. So no links to create.
[*]There is already [FONT=courier new]/etc/udev/rules.d/79-udev-epson.rules[/FONT] file with the above mentioned content.
[/LIST]
Any ideas?

---

### Post by Derspankster on 2018-08-18
WRONG! Not fixed with 18.04. I waited until I was notified that the upgrade was available with the hope that things like this would not be an issue. Wrong again. Love Ubuntu (12 years) but am getting sick of these types of issues.

---

### Post by rbmorse on 2018-08-18
I got tired of fighting with my old Epson 4490, too.  Finally coughed up the $79 to replace it with a Canon Canoscan LiDE 220.  Plug 'n Play with every Linux I've tried it on, and it's faster and quieter, too.  

Holds calibration better, too.

---

### Post by Kandersonnc on 2018-09-24
This fix is not working for me on an Epson GT-1500. Sane-find-scanner sees the scanner but scanimage -L and sudo scanimage -L do not. Scanner worked perfectly under Fedora 28 last week. I like Ubuntu 18.04 a lot and it seems to do everything quicker than Fedora was which is great. It also fixed a printing problem I was having in Fedora. Unfortunately, I now have 2 programs that did work under Fedora that I use daily that do not work in Ubuntu. Any other ideas on fixing this scanner issue?

Thanks
Ken

---

### Post by him610 on 2018-09-25
Not convinced there is really an issue with Epson scanners. Sometimes downloading and installing drivers then setting up the scanner can be complicated. 

FWIW, I have an Epson Perfection 1640 connected via USB to a system running Xubuntu 18.04.1. It also works on a system running Xubuntu 16.05.5.  The scan function using simple-scan works fine for me. 

There is a sane front end for Epson scanners. This is from the *man iscan*
```
ISCAN(1)                                            User Commands                                            ISCAN(1)

NAME
       iscan - Image Scan! for Linux SANE frontend

DESCRIPTION
       Image  Scan!  for  Linux (iscan) provides a graphical user-interface to control EPSON scanners.  It allows the
       previewing and scanning of images.  iscan can be invoked either from the  command-line  or  through  the  GIMP
       image manipulation program.

       When  run  from  the command line, iscan acts as a stand-alone program that saves acquired images in PNM, PNG,
       JPEG, TIFF, PCX or PDF format. Alternatively, acquired images can be sent directly to a printer, provided your
       print  system  handles  PNG  natively.   CUPS and Photo Image Print System, versions 1.3.1 and later, do this.
       LPRng and other LPD based printer systems may need a little help.  Refer to your print system's  documentation
       for  more information on how to set this up.  When run as a GIMP plugin, the images are passed to the GIMP for
       further processing.

       iscan accesses EPSON image acquisition devices through the SANE (Scanner Access Now Easy) interface.

RUNNING UNDER THE GIMP
       As of version 1.15.0, iscan is automatically registered as a gimp(1) plugin if you install the binary package.
       In case it didn't (because you built from source for example), you can register it yourself by creating a sym&#8208;
       bolic link from the iscan binary to one of the gimp(1) plug-ins directories. For example, for  gimp-1.2.x  the
       command

              ln -s /usr/bin/iscan ~/.gimp-1.2/plug-ins/

       adds  a symlink for the iscan binary to the user's plug-ins directory.  Your system administrator can register
       it for all users by creating a symbolic link in the gimp(1) system plug-ins directory.  After creating such  a
       symlink,  iscan  will  be  queried  by gimp(1) the next time it's invoked.  From then on, iscan can be invoked
       through "Xtns->Acquire Image->Scanning (iscan)" menu entry.

PRINTER SETUP
       When not using the default printer , it is necessary to input the printer name  from  /etc/printcap  into  the
       Print Command field of the Configuration dialog. For example, if the printer name is pm900c, input the follow&#8208;
       ing command.

              lpr -Ppm900c

EPSON Scan! for Linux WORKFLOW
       Use the following steps to scan an image with iscan.

              1. Select the document source.
              2. Select the image type.
              3. Preview the full page.
              4. Create a marquee (frame) of the image area to scan.
              5. Auto expose the selected area.
              6. Select the image destination.
              7. Scan the final image.

SEE ALSO
       gimp(1), gimptool(1), scanimage(1), sane-scsi(5), sane-dll(5), sane-net(5), sane-"backendname"(5)

AUTHOR
       Noriyoshi Sasaki and Peter Schretlen

Image Scan! for Linux                                 2011-10-19                                             ISCAN(1)
 
```

---

### Post by Kandersonnc on 2018-09-26
Well, I've mainly used Fedora the last few years and installing the scanner was as easy as installing the Epson iscan download from their site. After that the scanner worked. Scanimage -L immediately saw it, every scanning program
could see if and use it. I wanted to try Ubuntu 18.04 and went through the same process and everything seemed to install just fine just like under Fedora. Yet no scanning program can see the scanner. The "fixes" regarding creating the links and the udev rules have not worked. I guess I'm just a little confused and I'll admit, a little annoyed that the two most modern releases of Fedora and Ubuntu act so differently when dealing with the same hardware. Having the same oddity with Kopete messenger program. Trying to connect to an old server install (soon to be updated) and Kopete under Fedora connects just fine. Kopete under Ubuntu gives me TLS errors even though I've setup the user the exact same way under Fedora and Ubuntu. The scanner and messenger app I use on a daily basis at work and cannot be without them. I had no choice but to reinstall Fedora. We do have some spare PCs around here. Maybe I can put Ubuntu on one and see if I can ever get those working in my spare time. 

Thanks
Ken

---

### Post by bitinerant on 2018-09-27
I've struggled with this for most of the afternoon.  I think I've done everything correctly as described above and in bug #1728012, but my DS-30, which worked fine on 16.04, no longer works as a normal user. It *does* work as root. Here is my set-up. Do you see any problems?
[FONT=Lucida Console]
$ [COLOR=#0000ff]lsb_release -a[/COLOR]
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:    18.04
Codename:    bionic
$ [COLOR=#0000ff]scanimage -L[/COLOR]

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
$ [COLOR=#0000ff]sudo scanimage -L[/COLOR]
device `epkowa:interpreter:001:010' is a Epson DS-30 flatbed scanner
$ [COLOR=#0000ff]ls -l /usr/lib/sane[/COLOR]
total 296
-rw-r--r-- 1 root root    955 Jun 20  2016 libsane-epkowa.la
lrwxrwxrwx 1 root root     24 Jun 20  2016 libsane-epkowa.so.1 -> libsane-epkowa.so.1.0.15
-rw-r--r-- 1 root root 295080 Jun 20  2016 libsane-epkowa.so.1.0.15
$ [COLOR=#0000ff]ls -l /usr/lib/x86_64-linux-gnu/sane/libsane-epkowa*[/COLOR]
lrwxrwxrwx 1 root root 28 Sep 27 14:54 /usr/lib/x86_64-linux-gnu/sane/libsane-epkowa.la -> ../../sane/libsane-epkowa.la
lrwxrwxrwx 1 root root 35 Sep 27 14:54 /usr/lib/x86_64-linux-gnu/sane/libsane-epkowa.so.1 -> ../../sane/libsane-epkowa.so.1.0.15
lrwxrwxrwx 1 root root 35 Sep 27 14:54 /usr/lib/x86_64-linux-gnu/sane/libsane-epkowa.so.1.0.15 -> ../../sane/libsane-epkowa.so.1.0.15
$ [COLOR=#0000ff]ls -l /etc/udev/rules.d/79-udev-epson.rules[/COLOR]
-rw-r--r-- 1 root root 152 Sep 27 16:49 /etc/udev/rules.d/79-udev-epson.rules
$ [COLOR=#0000ff]cat /etc/udev/rules.d/79-udev-epson.rules[/COLOR]
# chmod device EPSON group
ATTRS{manufacturer}=="EPSON", DRIVERS=="usb", SUBSYSTEMS=="usb", ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="*", MODE="0777"
$ 
[/FONT]

---

### Post by marty777 on 2019-01-09
Here I am, struggling with an Epson ET-2500 with the scanner driver on Ubuntu Studio 18.10 (Xubuntu) (fresh Install).
Epson is delivering updates to the drivers regularly, but this does not help me (or us).:(

Finally I got it running, but maybe not like it was originally planned.
Here is what I have done. Hopefully you can also achieve at least a - I call it - emergency solution. ;)

I have downloaded the Epson scanner driver, for Ubuntu 18.10.

**imagescan-bundle-ubuntu-18.10-1.3.40.x64.deb.tar.gz**
unzipped, it gives a subdirectory with the install script. 
I installed it with this command

[B]$  tar xaf imagescan-bundle-ubuntu-18.10-1.3.40.x64.deb.tar.gz
$  cd imagescan-bundle-ubuntu-18.10-1.3.40.x64.deb
$ ./install.sh --without-network[/B]
(if you do not want the network plugin)

The result is this:
**$ apt list |grep epson**

[I]epson-inkjet-printer-escpr/now 1.6.33-1lsb3.2 amd64  [Installiert,lokal]
epson-printer-utility/now 1.0.2-1lsb3.2 amd64  [Installiert,lokal]
imagescan-plugin-gt-s650/now 1.0.0-1epson4ubuntu18.10 amd64  [Installiert,lokal]
imagescan-plugin-ocr-engine/now 1.0.0-1epson4ubuntu18.10 amd64  [Installiert,lokal]
imagescan/now 3.50.0-1epson4ubuntu18.10 amd64  [Installiert,lokal]
[/I]
Note, the package is now called imagescan, not iscan (maybe because I have an different printer/scanner than the others here).
Then restart the sane daemon.
**$ sudo /etc/init.d/saned restart**

Try to scan with **imagescan**. It is finding my Epson scanner, I can even scan an image (without preview), but when I try to save the document, nothing happens. No errors, no document created. No success.
Also **Simple Scan** does not find a scanner, and also **Xsane**, cannot find the scanner.

I tried the solution offered here, but it does not work (anymore?).

What does "apt" have to say to this imagescan package?
**$ apt show imagescan**[I]
Package: imagescan
Version: 3.50.0-1epson4ubuntu18.10
Status: install ok installed
Priority: optional
Section: graphics
Maintainer: SEIKO EPSON CORPORATION <linux-scanner@epson.jp>
Installed-Size: 9.011 kB
Depends: libatkmm-1.6-1v5 (>= 2.24.0), libboost-filesystem1.67.0, libboost-program-options1.67.0, libboost-system1.67.0, libc6 (>= 2.15), libgcc1 (>= 1:3.0), libglib2.0-0 (>= 2.12.0), libglibmm-2.4-1v5 (>= 2.54.0), libgraphicsmagick++-q16-12 (>= 1.3.26-5~), libgraphicsmagick-q16-3 (>= 1.3.11), libgtkmm-2.4-1v5 (>= 1:2.24.0), libjpeg8 (>= 8c), libltdl7 (>= 2.4.6), libpangomm-1.4-1v5 (>= 2.40.0), libsigc++-2.0-0v5 (>= 2.8.0), libstdc++6 (>= 6), libtiff5 (>= 4.0.3), libudev1 (>= 183), libusb-1.0-0 (>= 2:1.0.22), graphicsmagick
**Recommends: sane-utils**
**Suggests: tesseract (>= 3.03)**
Download-Size: unbekannt
APT-Manual-Installed: yes
APT-Sources: /var/lib/dpkg/status
Description: next generation image acquisition utilities
 This software provides applications to easily turn hard-copy
 documents and imagery into formats that are more amenable to
 computer processing.
 .
 Included are a native driver for a number of EPSON scanners
 and a compatibility driver to interface with software built
 around the SANE standard.[/I]

sane-utils was installed by the install script, but there is suggestion to install a **tesseract **package.
OK, so then I installed these 2 packages:
[B]$ sudo apt-get install xsane
$ sudo apt-get install sane
$ sudo adduser $USER lp
$ sudo adduser $USER scanner[/B]
**$ vi /etc/sane.d/dll.conf **
comment out the epson lines:
    [I]epson2&#12288;->&#12288;  #epson2
    epsonds&#12288;->    #epsonds[/I]

the suggested changes to lib directories was not necessary (all OK).
**a) check if your epson lib is here:**
*/usr/lib/x86_64-linux-gnu/sane'*
**b) check if '/etc/udev/rules.d/79-udev-epson.rules'**
content:[I]
# chmod device EPSON group
ATTRS{manufacturer}=="EPSON", DRIVERS=="usb", SUBSYSTEMS=="usb", ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="*", MODE="0777"[/I]

Restart the sane daemon, or reboot.
**$ sudo /etc/init.d/saned restart**

Check if scanner is found now:
**$ scanimage -L**
*device `imagescan:esci:usb:/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.0' is a EPSON EPSON_ET-2500_Series *

Great!
This solves my issue with the scanner partly. The **imagescan** program and **simple-scan**, do **not work** anything better.
But, **xsane** is working just well (one caveat: no preview) now.
And also the **scanimage** command line utility is working (Note if scanimage is finding your printer, it should also be possible to  scan with this program. That is an emergency solution, if nothing else  works. On my old 16.04 LTS Installation, that was the only thing that I managed to get running.).
However, xsane is the better program (more options), than imagescan and simple-scan. At least I am happy, that I can use the scanner now. 

Hopefully, this will help some others, too.

---

### Post by alchemist0 on 2019-01-29
> **ivo.kovacic.sk said:**
> Solution can be found here
[https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/1728012](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/1728012)
See post #25 - [TABLE]
[TR]
[TD][staedtler-przyborski (staedtler-przyborski)]("https://launchpad.net/~staedtler-przyborski") wrote on 2017-11-03:[/TD]
[TD="class: bug-comment-index"][#25]("https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/1728012/comments/25")[/TD]
[/TR]
[/TABLE]

[COLOR=#333333][FONT=monospace]Epson Iscan[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]a) 'sudo ln -sfr /usr/lib/sane/libsane-epkowa* /usr/lib/x86_64-linux-gnu/sane'
b) generate '/etc/udev/rules.d/79-udev-epson.rules'
content:
# chmod device EPSON group
ATTRS{manufacturer}=="EPSON", DRIVERS=="usb", SUBSYSTEMS=="usb", ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="*", MODE="0777"

I have used it for Epson V370 and it is working.
I consider it verified.
V Ubuntu 18.04 64 bit used and upgraded since 14.04, running on Asus X550C.[/FONT][/COLOR]
Thanks a lot! :)

---

### Post by donanpher on 2019-06-22
Thanks a lot, you are so great...., you've made me very very happy!!! [IMG]https://ubuntuforums.org/images/icons/icon11.png[/IMG][IMG]https://ubuntuforums.org/images/icons/icon6.png[/IMG]

> **ivo.kovacic.sk said:**
> Solution can be found here
[https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/1728012](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/1728012)
See post #25 - [TABLE]
[TR]
[TD][staedtler-przyborski (staedtler-przyborski)]("https://launchpad.net/~staedtler-przyborski") wrote on 2017-11-03:[/TD]
[TD="class: bug-comment-index"][#25]("https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/1728012/comments/25")[/TD]
[/TR]
[/TABLE]

[COLOR=#333333][FONT=monospace]Epson Iscan[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]a) 'sudo ln -sfr /usr/lib/sane/libsane-epkowa* /usr/lib/x86_64-linux-gnu/sane'
b) generate '/etc/udev/rules.d/79-udev-epson.rules'
content:
# chmod device EPSON group
ATTRS{manufacturer}=="EPSON", DRIVERS=="usb", SUBSYSTEMS=="usb", ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="*", MODE="0777"

I have used it for Epson V370 and it is working.
I consider it verified.
V Ubuntu 18.04 64 bit used and upgraded since 14.04, running on Asus X550C.[/FONT][/COLOR]

---

### Post by kenubix on 2019-08-08
> **marty777 said:**
> Here I am, struggling with an Epson ET-2500 with the scanner driver on Ubuntu Studio 18.10 (Xubuntu) (fresh Install).
Epson is delivering updates to the drivers regularly, but this does not help me (or us).:(

Finally I got it running, but maybe not like it was originally planned.
Here is what I have done. Hopefully you can also achieve at least a - I call it - emergency solution. ;)

I have downloaded the Epson scanner driver, for Ubuntu 18.10.

**imagescan-bundle-ubuntu-18.10-1.3.40.x64.deb.tar.gz**
unzipped, it gives a subdirectory with the install script. 
I installed it with this command

[B]$  tar xaf imagescan-bundle-ubuntu-18.10-1.3.40.x64.deb.tar.gz
$  cd imagescan-bundle-ubuntu-18.10-1.3.40.x64.deb
$ ./install.sh --without-network[/B]
(if you do not want the network plugin)

The result is this:
**$ apt list |grep epson**

[I]epson-inkjet-printer-escpr/now 1.6.33-1lsb3.2 amd64  [Installiert,lokal]
epson-printer-utility/now 1.0.2-1lsb3.2 amd64  [Installiert,lokal]
imagescan-plugin-gt-s650/now 1.0.0-1epson4ubuntu18.10 amd64  [Installiert,lokal]
imagescan-plugin-ocr-engine/now 1.0.0-1epson4ubuntu18.10 amd64  [Installiert,lokal]
imagescan/now 3.50.0-1epson4ubuntu18.10 amd64  [Installiert,lokal]
[/I]
Note, the package is now called imagescan, not iscan (maybe because I have an different printer/scanner than the others here).
Then restart the sane daemon.
**$ sudo /etc/init.d/saned restart**

Try to scan with **imagescan**. It is finding my Epson scanner, I can even scan an image (without preview), but when I try to save the document, nothing happens. No errors, no document created. No success.
Also **Simple Scan** does not find a scanner, and also **Xsane**, cannot find the scanner.

I tried the solution offered here, but it does not work (anymore?).

What does "apt" have to say to this imagescan package?
**$ apt show imagescan**[I]
Package: imagescan
Version: 3.50.0-1epson4ubuntu18.10
Status: install ok installed
Priority: optional
Section: graphics
Maintainer: SEIKO EPSON CORPORATION <linux-scanner@epson.jp>
Installed-Size: 9.011 kB
Depends: libatkmm-1.6-1v5 (>= 2.24.0), libboost-filesystem1.67.0, libboost-program-options1.67.0, libboost-system1.67.0, libc6 (>= 2.15), libgcc1 (>= 1:3.0), libglib2.0-0 (>= 2.12.0), libglibmm-2.4-1v5 (>= 2.54.0), libgraphicsmagick++-q16-12 (>= 1.3.26-5~), libgraphicsmagick-q16-3 (>= 1.3.11), libgtkmm-2.4-1v5 (>= 1:2.24.0), libjpeg8 (>= 8c), libltdl7 (>= 2.4.6), libpangomm-1.4-1v5 (>= 2.40.0), libsigc++-2.0-0v5 (>= 2.8.0), libstdc++6 (>= 6), libtiff5 (>= 4.0.3), libudev1 (>= 183), libusb-1.0-0 (>= 2:1.0.22), graphicsmagick
**Recommends: sane-utils**
**Suggests: tesseract (>= 3.03)**
Download-Size: unbekannt
APT-Manual-Installed: yes
APT-Sources: /var/lib/dpkg/status
Description: next generation image acquisition utilities
 This software provides applications to easily turn hard-copy
 documents and imagery into formats that are more amenable to
 computer processing.
 .
 Included are a native driver for a number of EPSON scanners
 and a compatibility driver to interface with software built
 around the SANE standard.[/I]

sane-utils was installed by the install script, but there is suggestion to install a **tesseract **package.
OK, so then I installed these 2 packages:
[B]$ sudo apt-get install xsane
$ sudo apt-get install sane
$ sudo adduser $USER lp
$ sudo adduser $USER scanner[/B]
**$ vi /etc/sane.d/dll.conf **
comment out the epson lines:
    [I]epson2&#12288;->&#12288;  #epson2
    epsonds&#12288;->    #epsonds[/I]

the suggested changes to lib directories was not necessary (all OK).
**a) check if your epson lib is here:**
*/usr/lib/x86_64-linux-gnu/sane'*
**b) check if '/etc/udev/rules.d/79-udev-epson.rules'**
content:[I]
# chmod device EPSON group
ATTRS{manufacturer}=="EPSON", DRIVERS=="usb", SUBSYSTEMS=="usb", ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="*", MODE="0777"[/I]

Restart the sane daemon, or reboot.
**$ sudo /etc/init.d/saned restart**

Check if scanner is found now:
**$ scanimage -L**
*device `imagescan:esci:usb:/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.0' is a EPSON EPSON_ET-2500_Series *

Great!
This solves my issue with the scanner partly. The **imagescan** program and **simple-scan**, do **not work** anything better.
But, **xsane** is working just well (one caveat: no preview) now.
And also the **scanimage** command line utility is working (Note if scanimage is finding your printer, it should also be possible to  scan with this program. That is an emergency solution, if nothing else  works. On my old 16.04 LTS Installation, that was the only thing that I managed to get running.).
However, xsane is the better program (more options), than imagescan and simple-scan. At least I am happy, that I can use the scanner now. 

Hopefully, this will help some others, too.

=======================
root@abaki5:/alt/packages_ubu# apt list | grep epson

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

imagescan/now 3.57.0-1epson4ubuntu18.04 amd64 [zainstalowany,lokalny]
imagescan-plugin-gt-s650/now 1.0.1-1epson4ubuntu18.04 amd64 [zainstalowany,lokalny]
imagescan-plugin-networkscan/now 1.1.2-1epson4ubuntu18.04 amd64 [zainstalowany,lokalny]
imagescan-plugin-ocr-engine/now 1.0.1-1epson4ubuntu18.04 amd64 [zainstalowany,lokalny]
root@abaki5:/alt/packages_ubu# lsb
lsblk        lsb_release  
root@abaki5:/alt/packages_ubu# lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.3 LTS
Release:    18.04
Codename:    bionic
root@abaki5:/alt/packages_ubu# uname -a
Linux abaki5 4.15.0-55-generic #60-Ubuntu SMP Tue Jul 2 18:22:20 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
root@abaki5:/alt/packages_ubu# 

=========================

Scanner - Epson Perfect V19 usb (  ... 0x13c)

2019.08.08, Ubuntu updated.
I have identical program behavior.
Commenting on "# epson2 / # epson" in dll.conf has no effect.
   It still works the same.
"Iscanimage" works without writing. "Xsane" works without preview.

---

### Post by kenubix on 2019-08-09
> **kenubix said:**
> =======================
root@abaki5:/alt/packages_ubu# apt list | grep epson

imagescan/now 3.57.0-1epson4ubuntu18.04 amd64 [zainstalowany,lokalny]
imagescan-plugin-gt-s650/now 1.0.1-1epson4ubuntu18.04 amd64 [zainstalowany,lokalny]
imagescan-plugin-networkscan/now 1.1.2-1epson4ubuntu18.04 amd64 [zainstalowany,lokalny]
imagescan-plugin-ocr-engine/now 1.0.1-1epson4ubuntu18.04 amd64 [zainstalowany,lokalny]


[.... cut ....]
=========================

Scanner - Epson Perfect V19 usb (  ... 0x13c)

2019.08.08, Ubuntu updated.
I have identical program behavior.
Commenting on "# epson2 / # epson" in dll.conf has no effect.
   It still works the same.
"Iscanimage" works without writing. "Xsane" works without preview.

UPDATE:
I uninstalled through synaptic all the "iscanimage" and "iscan" packages used previously.
I downloaded (from epson) the iscan-gt-s650-boundle-1.0.1.x64.deb version.
I installed "./install.sh --without-network".
I did not delete "/etc/udev/rules.d/79-udev-epson.rules"
:) works "xsane" (with preview), iscan, simple-scan, ..

ps.
root@abaki5:/alt/packages_ubu/scaner-epson-v19# scanimage -L
device `epkowa:interpreter:001:006' is a Epson Perfection V19 flatbed scanner

---

### Post by david503 on 2019-08-22
I read all the comments here I still can't get it to work.  I downloaded and ran the install.sh with no errors. How am I still getting this:

I have an Epson v37 scanner:

I'm in 18.04

```




bog@bog-Lenovo-Product:~/Downloads/imagescan-bundle-ubuntu-18.04-3.59.2.x64.deb$ lsusb | grep Epso
Bus 003 Device 008: ID 04b8:014a Seiko Epson Corp.
bog@bog-Lenovo-Product:~/Downloads/imagescan-bundle-ubuntu-18.04-3.59.2.x64.deb$ sudo sane-find-scanner


  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.


  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.


found USB scanner (vendor=0x04b8 [EPSON], product=0x014a [EPSON Perfection V37/V370]) at libusb:003:008
could not fetch string descriptor: Pipe error
could not fetch string descriptor: Pipe error
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.


  # Not checking for parallel port scanners.


  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
bog@bog-Lenovo-Product:~/Downloads/imagescan-bundle-ubuntu-18.04-3.59.2.x64.deb$ scanimage -L


No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
bog@bog-Lenovo-Product:~/Downloads/imagescan-bundle-ubuntu-18.04-3.59.2.x64.deb$

```

---

### Post by cscj01 on 2019-09-05
I have an Epson Perfection V600 Photo.  I spent three days trying to solve this.  I found my solution today here: [https://askubuntu.com/questions/1038557/ubuntu-18-04-scanner-program-does-not-detect-scanner]("https://askubuntu.com/questions/1038557/ubuntu-18-04-scanner-program-does-not-detect-scanner")

All I needed was the first answer then all my scanning programs worked: Vuescan, Image Scan for Linux, Simple Scan, and Xsane.  Good luck.

---

### Post by tyoung81 on 2019-10-05
I am also having troubles. I just tried installing the driver for Epson Workforce DS-30 Portable Scanner on a fresh install of Ubuntu Mate 18.04. When I try to open Imagescan for Linux, I am getting the error, can't connect to scanner. And when I go into simple scan, I am getting the error, no scanners available. I have tried the "solution" found in this thread that several others have stated that worked for them, but with no luck. Below, is my output for lsusb, sane-find-scanner, and scanimage -L; any help/suggestions would be greatly appreciated.


tricia@tricia-TECRA-C40-D:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 8087:0a2b Intel Corp. 
Bus 001 Device 004: ID 04f2:b446 Chicony Electronics Co., Ltd 
**Bus 001 Device 008: ID 04b8:0147 Seiko Epson Corp. **
Bus 001 Device 002: ID 0e8d:1887 MediaTek Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
tricia@tricia-TECRA-C40-D:~$ sudo sane-find-scanner
[sudo] password for tricia: 

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

**found USB scanner (vendor=0x04b8 [Seiko Epson Corp. ], product=0x0147 [EPSON DS-30        ]) at libusb:001:008**
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
tricia@tricia-TECRA-C40-D:~$ sudo scanimage -L
[B]device `epkowa:interpreter:001:008' is a Epson DS-30 flatbed scanner
[/B]

---

### Post by brian_p on 2019-10-06
The DS-30 uses iscan, not imagescan.

---

### Post by tyoung81 on 2019-10-10
> **brian_p said:**
> The DS-30 uses iscan, not imagescan.

I downloaded the driver from Epson's website after putting my model, ds-30, into the search: [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=97923&DSCCHK=8b4555592df0b197586b3158f8342bbbad065d0c](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=97923&DSCCHK=8b4555592df0b197586b3158f8342bbbad065d0c). However, what was installed, as stated in the menu is: "Image Scan! for Linux", to which I was referring to in my previous post. However, I assure you that the package name downloaded is iscan.

---

### Post by brian_p on 2019-10-10
> **tyoung81 said:**
> I downloaded the driver from Epson's website after putting my model, ds-30, into the search: [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=97923&DSCCHK=8b4555592df0b197586b3158f8342bbbad065d0c](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=97923&DSCCHK=8b4555592df0b197586b3158f8342bbbad065d0c). However, what was installed, as stated in the menu is: "Image Scan! for Linux", to which I was referring to in my previous post. However, I assure you that the package name downloaded is iscan.

I am reassured. :)

I am perplexed. Your *scanimage -L* says that SANE has found a driver for your scanner. Typing ```
iscan
``` in a terminal should open the Epson program.

How do you on with ```
scanimage -d epkowa:interpreter:001:008 > image.pnm
```

Check that 001:008 hasn't changed.

---

### Post by tyoung81 on 2019-10-10
> I am perplexed. Your *scanimage -L* says that SANE has found a driver for your scanner. Typing  	Code:
 	iscan 
 in a terminal should open the Epson program.

How do you on with  	Code:
 	scanimage -d epkowa:interpreter:001:008 > image.pnm 
Check that 001:008 hasn't changed.

When I type iscan in the terminal, I still get the error popup: "Could not send command to scanner. Check scanner status."

Also I entered scanimage -d epkowa:interpreter:001:008 > image.pnm into terminal. See my results below:

tricia@tricia-TECRA-C40-D:~$ scanimage -d epkowa:interpreter:001:008 > image.pnm
scanimage: open of device epkowa:interpreter:001:008 failed: Access to resource has been denied
tricia@tricia-TECRA-C40-D:~$ 

So I tried that last command again, with sudo:

tricia@tricia-TECRA-C40-D:~$ sudo scanimage -d epkowa:interpreter:001:008 > image.pnm
[sudo] password for tricia: 
scanimage: open of device epkowa:interpreter:001:008 failed: Invalid argument

---

### Post by brian_p on 2019-10-11
> **tyoung81 said:**
> When I type iscan in the terminal, I still get the error popup: "Could not send command to scanner. Check scanner status."

Also I entered scanimage -d epkowa:interpreter:001:008 > image.pnm into terminal. See my results below:

tricia@tricia-TECRA-C40-D:~$ scanimage -d epkowa:interpreter:001:008 > image.pnm
scanimage: open of device epkowa:interpreter:001:008 failed: Access to resource has been denied
tricia@tricia-TECRA-C40-D:~$ 

Your user has the necessary permissions to access the USB bus, otherwise she would have had a negative reponse from *sane-find-scanner*. Please see [https://wiki.debian.org/Scanner](https://wiki.debian.org/Scanner).

> 
So I tried that last command again, with sudo:

tricia@tricia-TECRA-C40-D:~$ sudo scanimage -d epkowa:interpreter:001:008 > image.pnm
[sudo] password for tricia: 
scanimage: open of device epkowa:interpreter:001:008 failed: Invalid argument

So, this cannot be about permissions. *Invalid argument* is a little vague, isn't it? Now for a stab in the dark! Edit */usr/lib/udev/hwdb.d/ iscan-data.hwdb* to have ```
usb:v04B8p0147*                                                                                                             
 libsane_matched=yes
``` added, check that 001:008 is unchanged and try scanning again.

---

### Post by david503 on 2019-10-12
Yea this is what finally worked for me- I downloaded the iscan package:

 iscan-perfection-v370-bundle-2.30.4.x64.deb
from here: 

[http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)

Or btw if that's a session then try this: 

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=97922&DSCCHK=124e3d9dad056ef17ac0667abb5d9b0b1bb9c980](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=97922&DSCCHK=124e3d9dad056ef17ac0667abb5d9b0b1bb9c980)

I ran the install.sh as root

I had done that before but for some reason this time it worked!  I think what was missing is that I had to cycle the scanner's power.

As was said above- You'll find "Image Scan for linux" in your Graphics applications menu in gnome.  

Woo!

---

### Post by brian_p on 2019-10-13
> **brian_p said:**
> 
 Edit */usr/lib/udev/hwdb.d/ iscan-data.hwdb* to have ```
usb:v04B8p0147*                                                                                                             
 libsane_matched=yes
``` added, check that 001:008 is unchanged and try scanning again.

Wouldn't it be nice if this suggestion was commented on? You never know - the response might help someone else, whether it works or not.

---

