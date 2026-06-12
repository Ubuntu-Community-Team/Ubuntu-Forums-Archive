---
title: "dpkg was interrupted, you must manu...."
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by morehands on 2009-02-10
I know this looks like a moron first post but i have looked extensively through the forums for a solution and i cant find one!

im using 9.04 and i first noticed that there were problems installing Amarok, and there seems to be a problem installing anything now, from add/remove and apt get

i tried:
> **nowshining said:**
> try again after:

```
sudo apt-get autoremove
```

Then try again after:

```
sudo apt-get autoclean
```

then try:
```

Sudo apt-get clean
```

then if u still have probs, try the dpkg -a or whatever it asked u to do..if all else fails try to logout and backin - if that fails - try a reboot...

and nothing, when i run

```
sudo dpkg --configure -a
```

in that it seems to not have errors:
> e@e-desktop:~$ sudo dpkg --configure -a
e@e-desktop:~$ 


on
```
sudo apt-get upgrade
```
everything seems to install fine, takes a few minutes but at the end i get:
> Fetched 105MB in 2min0s (869kB/s)                                                  
Extracting templates from packages: 100%
Preconfiguring packages ...
debconf: DbDriver "templatedb": rename failed: Operation not permitted
(Reading database ... dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd): files list for package `libwps-0.1-1': Invalid argument
E: Sub-process /usr/bin/dpkg returned an error code (2)



its driving me nuts, i cant get upgrades, pro grammes etc and im stumped




also i tried
```

e@e-desktop:~$ sudo dpkg -l | grep -v ^ii 
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                       Version                                 Description
+++-==========================================-=======================================-============================================
rc  bluez-audio                                3.26-0ubuntu6                           Bluetooth audio support
rc  console-tools                              1:0.2.3dbs-65ubuntu7                    Linux console and font utilities
ri  cups-driver-gutenprint                     5.2.3-0ubuntu1                          printer drivers for CUPS
rc  cups-pdf                                   2.4.8-1ubuntu1                          PDF printer for CUPS
ri  cupsys-driver-gutenprint                   5.2.3-0ubuntu1                          Transitional package
rc  dhcdbd                                     3.0-1ubuntu1                            D-Bus interface to the ISC DHCP client
rc  evolution                                  2.24.3-0ubuntu1                         groupware suite with mail client and organiz
rc  evolution-exchange                         2.24.3-0ubuntu1                         Exchange plugin for the Evolution groupware 
rc  liba52-0.7.4                               0.7.4-11ubuntu1                         library for decoding ATSC A/52 streams
rc  libbind9-30                                1:9.4.2.dfsg.P2-2ubuntu0.1              BIND9 Shared Library used by BIND
rc  libbluetooth2                              3.29-0ubuntu1                           Library to use the BlueZ Linux Bluetooth sta
rc  libcamel1.2-11                             2.22.3-0ubuntu2                         The Evolution MIME message handling library
rc  libchromexvmc1                             1:0.2.901-0ubuntu4                      XvMC Libraries used by the Openchrome VIA dr
rc  libchromexvmcpro1                          1:0.2.901-0ubuntu4                      XvMC Pro Libraries used by the Openchrome VI
rc  libdjvulibre15                             3.5.20-2                                Runtime support for the DjVu image format
rc  libdns32                                   1:9.4.2-10                              DNS Shared Library used by BIND
rc  libdns35                                   1:9.4.2.dfsg.P2-2ubuntu0.1              DNS Shared Library used by BIND
rc  libdvdnav4                                 4.1.2-3                                 DVD navigation library
rc  libdvdread3                                0.9.7-11ubuntu3                         library for reading DVDs
rc  libedataserver1.2-9                        2.22.3-0ubuntu2                         Utility library for evolution data servers
rc  libffi4                                    4.2.4-1ubuntu3                          Foreign Function Interface library runtime
rc  libgda3-3                                  3.0.2-5ubuntu1                          GNOME Data Access library for GNOME2
rc  libgda3-common                             3.0.2-5ubuntu1                          Common files for GNOME Data Access library f
rc  libgmime-2.0-2                             2.2.11-2ubuntu1                         MIME library
rc  libgnome-desktop-2                         1:2.22.3-0ubuntu1                       Utility library for loading .desktop files -
rc  libgnome-desktop-2-7                       1:2.24.1-0ubuntu1                       Utility library for loading .desktop files -
rc  libgnomedb3-4                              3.0.0-4build1                           Database UI widget library for GNOME2
rc  libgnomedb3-common                         3.0.0-4build1                           Database UI widget library for GNOME2 -- com
rc  libgnomekbd2                               2.22.0-1                                GNOME library to manage keyboard configurati
rc  libgnomekbdui2                             2.22.0-1                                User interface library for libgnomekbd - sha
rc  libgnutls13                                2.0.4-1ubuntu2.3                        the GNU TLS library - runtime library
rc  libgoffice-0-6                             0.6.5-1ubuntu1                          Document centric objects library - runtime f
rc  libgpmg1                                   1.19.6-25ubuntu1                        General Purpose Mouse - shared library
rc  libgsf-gnome-1-114                         1.14.11-1ubuntu1                        Structured File Library - runtime version fo
rc  libgtkglext1                               1.2.0-1ubuntu1                          OpenGL Extension to GTK+ (shared libraries)
rc  libgtkhtml-editor0                         1:3.25.90-0ubuntu1                      HTML rendering/editing library - editor widg
rc  libgucharmap6                              1:2.22.1-0ubuntu2                       Unicode browser widget library (shared libra
rc  libhunspell-1.1-0                          1.1.9-1                                 spell checker and morphological analyzer (sh
rc  libid3tag0                                 0.15.1b-10                              ID3 tag reading library from the MAD project
rc  libisc32                                   1:9.4.2-10ubuntu0.1                     ISC Shared Library used by BIND
rc  libisc35                                   1:9.4.2.dfsg.P2-2ubuntu0.1              ISC Shared Library used by BIND
rc  libisccc30                                 1:9.4.2.dfsg.P2-2ubuntu0.1              Command Channel Library used by BIND
rc  libisccfg30                                1:9.4.2.dfsg.P2-2ubuntu0.1              Config File Handling Library used by BIND
rc  libloudmouth1-0                            1.4.2-2                                 Lightweight C Jabber library
rc  libltdl3                                   1.5.26-1ubuntu1                         A system independent dlopen wrapper for GNU 
rc  liblwres30                                 1:9.4.2.dfsg.P2-2ubuntu0.1              Lightweight Resolver Library used by BIND
ri  libmad0                                    0.15.1b-4                               MPEG audio decoder library
rc  libmagick10                                7:6.3.7.9.dfsg1-2ubuntu3                image manipulation library
rc  libmpeg2-4                                 0.4.1-3                                 MPEG1 and MPEG2 video decoder library
rc  libmtp7                                    0.2.6.1-2ubuntu1                        Media Transfer Protocol (MTP) library
rc  libnm-util0                                0.7~~svn20081018t105859-0ubuntu1.8.10.1 network management framework (shared library
rc  libntfs-3g23                               1:1.2216-1ubuntu2                       ntfs-3g filesystem in userspace (FUSE) libra
rc  libntfs-3g28                               1:1.2506-1ubuntu2                       ntfs-3g filesystem in userspace (FUSE) libra
rc  libopal-2.2                                2.2.11~dfsg1-4ubuntu1                   Open Phone Abstraction Library - successor o
rc  libopenal0a                                1:0.0.8-7                               OpenAL is a portable library for 3D spatiali
rc  libopencdk10                               0.6.6-1ubuntu1                          Open Crypto Development Kit (OpenCDK) (runti
rc  libopenexr2ldbl                            1.2.2-4.4ubuntu1                        runtime files for the OpenEXR image library
rc  libparted1.7-1                             1.7.1-5.1ubuntu9.1                      The GNU Parted disk partitioning shared libr
rc  libparted1.8-9                             1.8.8.git.2008.03.24-7ubuntu7           The GNU Parted disk partitioning shared libr
rc  libpoppler-glib2                           0.6.4-1ubuntu3.1                        PDF rendering library (GLib-based shared lib
rc  libpoppler2                                0.6.4-1ubuntu3.1                        PDF rendering library
rc  libpulsecore5                              0.9.10-2ubuntu9.3                       PulseAudio sound server core
rc  libsidplay1                                1.36.59-5                               SID (MOS 6581) emulation library
rc  libsmbios1                                 0.13.10-1ubuntu1.1                      Provide access to (SM)BIOS information -- dy
rc  libtotem-plparser10                        2.22.3-0ubuntu2                         Totem Playlist Parser library - runtime vers
rc  libxcb-xlib0                               1.1-1.1                                 X C Binding, Xlib/XCB interface library
rc  linux-image-2.6.24-16-generic              2.6.24-16.30                            Linux kernel image for version 2.6.24 on x86
rc  linux-restricted-modules-2.6.24-16-generic 2.6.24.12-16.34                         Non-free Linux 2.6.24 modules on x86/x86_64
rc  linux-ubuntu-modules-2.6.24-16-generic     2.6.24-16.23                            Ubuntu supplied Linux modules for version 2.
rc  myspell-en-us                              1:2.4.0~m240-1ubuntu1                   English_american dictionary for myspell
rc  powermanagement-interface                  0.3.18                                  platform neutral powermanagement interface
rc  scrollkeeper                               0.3.14-15ubuntu1                        A free electronic cataloging system for docu
ri  ubuntu-standard                            1.132                                   The Ubuntu standard system
rc  xserver-xorg-video-via                     1:0.2.2-5                               X.Org X server -- VIA display driver

```

not sure if this helps or makes this even more confused!

---

### Post by oldos2er on 2009-02-10
If you're running Jaunty, look for help here: [http://ubuntuforums.org/forumdisplay.php?f=352](http://ubuntuforums.org/forumdisplay.php?f=352)

---

