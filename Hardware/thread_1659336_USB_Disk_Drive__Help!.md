---
title: "USB Disk Drive  Help!"
date: 2011-01-03
forum: Hardware
---

### Post by eksivus on 2011-01-03
Hello community,
 
(HP Mini110-3000)
(Ubuntu 10.10 Netbook Remix)
(Disc Drive Pioneer DVR-XD10)
 
I just bought an external DVD/CD drive for my wife for her Windows netbook. I'm wondering what packages should I install so that my computer can use the external disk drive. As it stands, any disks that I put in it can't be read: an error screen appears saying that the source can't be found.
 
Is there a certain package that I can download to render the disk drive usable?
Do i need a Linux version of Nero to use it?
 
I am very new to Ubuntu and Linux. So please be as clear as possible.
 
Any help appreciated.

---

### Post by damphoud on 2011-01-03
I'm not sure if I'll be of any help, but could you post the output of lsusb?

---

### Post by eksivus on 2011-01-04
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 08e4:0150 Pioneer Corp. 
Bus 001 Device 003: ID 1fea:0047  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by eksivus on 2011-01-04
Well, my computer is finding the drive I guess. I've been messing around in the file manager, I can select bits of DVDs but they don't play. Also, I found that selecting the VTS files is when the error message says the source cant be found. The video_TS .VOB show an image but say that the dvds "don't play in this region". I have no idea what that means.

---

### Post by SaintDanBert on 2011-01-04
[highlight]Playing[/highlight] a commercial DVD or CD is a separate issue from access to the drive itself.

Grab any software media that you have handy. Load it.
Can you see files and folders?  Can you open any html files with a browser? Can you open image files with a pic viewer? Can you open any 
PDF files with a document viewer?  If yes, then your drive and friends likely are working fine.

"Playing" media files require software called "codecs". The bits on disk are packed and compressed and twisted in various ways for various reasons by various vendors. Each variation requires a unique and sometimes conflicting edition of codecs.  (Consider the issue of iTunes(tm) v. WAV vs. MP3 on win-doze.)

Solving troubles with codecs involves two things:  technology and "the law".  The technolgy exists to read and write most of the existing formats. You need only load the packages that you need for the formats you want to use. "The law" gets involved because of DRM {I call it "distribution rights management",but ...} and copyright enforcement.
Rules vary by jurisdiction and country and so you are able to load codec software but the distro and device makers cannot do that for you. If you do it, and there are legal tangles, it is up to you to play nice. 

There are too many codec loading postings online to list.

Bonne Chance,
~~~ 0;-Dan

---

### Post by eksivus on 2011-01-04
Thanks a ton!
 
I grabbed some media and indeed I can access files from the discs. I am just unable to play the media. I have downloaded the codecs from a Gswinger package.( Not Gswinger but something like that, it begins with a G.) How would I go into the terminal and make sure the codecs are actually loaded?

---

### Post by SaintDanBert on 2011-01-06
Try the command:
```

prompt$ [color=green]sudo dpkg --list | less --ignore-case[/color]

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                       Version                                               Description
+++-==========================================-=====================================================-==========================================================
ii  2vcard                                     0.5-3                                                 perl script to convert an addressbook to VCARD file format
ii  a2ps                                       1:4.14-1                                              GNU a2ps - 'Anything to PostScript' converter and pretty-p
ii  acpi                                       1.4-2                                                 displays information on ACPI devices
ii  acpi-support                               0.136.1                                               scripts for handling many ACPI events
ii  acpid                                      1.0.10-5ubuntu2.1                                     Advanced Configuration and Power Interface event daemon
ii  acpidump                                   20071116-1                                            utilities to dump system's ACPI tables to an ASCII file
ii  acpitail                                   0.1-3                                                 Show ACPI information in a tail-like style
ii  acpitool                                   0.5-7                                                 command line ACPI client
ii  adblock-plus                               1.1.3-1build1                                         transitional dummy package
ii  add-apt-key                                1.0-0.5                                               Command line tool to add GPG keys to the APT keyring
...
ii  xserver-xorg-video-radeon                  1:6.13.0-1ubuntu5                                     X.Org X server -- AMD/ATI Radeon display driver
ii  xserver-xorg-video-rendition               1:4.2.3-1                                             X.Org X server -- Rendition display driver
ii  xserver-xorg-video-s3                      1:0.6.3-1                                             X.Org X server -- legacy S3 display driver
ii  xserver-xorg-video-s3virge                 1:1.10.4-1                                            X.Org X server -- S3 ViRGE display driver
ii  xserver-xorg-video-savage                  1:2.3.1-1ubuntu1                                      X.Org X server -- Savage display driver
ii  xserver-xorg-video-siliconmotion           1:1.7.3-1                                             X.Org X server -- SiliconMotion display driver
ii  xserver-xorg-video-sis                     1:0.10.2-2                                            X.Org X server -- SiS display driver
ii  xserver-xorg-video-sisusb                  1:0.9.3-1                                             X.Org X server -- SiS USB display driver
ii  xserver-xorg-video-tdfx                    1:1.4.3-1                                             X.Org X server -- tdfx display driver
ii  xserver-xorg-video-trident                 1:1.3.3-1                                             X.Org X server -- Trident display driver
ii  xserver-xorg-video-tseng                   1:1.2.3-1                                             X.Org X server -- Tseng display driver
ii  xserver-xorg-video-v4l                     1:0.2.0-4                                             X.Org X server -- Video 4 Linux display driver
ii  xserver-xorg-video-vesa                    1:2.3.0-1ubuntu1                                      X.Org X server -- VESA display driver
ii  xserver-xorg-video-vmware                  1:10.16.9-1                                           X.Org X server -- VMware display driver
ii  xserver-xorg-video-voodoo                  1:1.2.3-1                                             X.Org X server -- Voodoo display driver
ii  xsltproc                                   1.1.26-1ubuntu1                                       XSLT command line processor
ii  xsmbrowser                                 3.4.0-16.1ubuntu1                                     X11 tool for navigating SMB Networks
ii  xterm                                      256-1ubuntu1                                          X terminal emulator
ii  xtrans-dev                                 1.2.5-1                                               X transport library (development files)
ii  xul-ext-adblock-plus                       1.1.3-1build1                                         Advertisement blocking extension for web browsers
ii  xulrunner-1.9.2                            1.9.2.13+build3+nobinonly-0ubuntu0.10.04.1            XUL + XPCOM application runner
ii  xz-utils                                   4.999.9beta+20091116-1                                XZ-format compression utilities
ii  yacpi                                      3.0-2                                                 ncurses based acpi monitor for text mode
ii  yelp                                       2.30.0-0ubuntu2                                       Help browser for GNOME
ii  zenity                                     2.30.0-0ubuntu1                                       Display graphical dialog boxes from shell scripts
ii  zim                                        0.43-2                                                graphical text editor based on wiki technologies
ii  zip                                        3.0-2                                                 Archiver for .zip files
ii  zlib1g                                     1:1.2.3.3.dfsg-15ubuntu1                              compression library - runtime
(END)

```

You can then use "/pattern" within the **less** find whichever packages you seek.  With the --ignore-case option, type your pattern using lower case and less finds upper or lower strings that match. If you type uppercase in your pattern then less respects what you typed during the search. You could also pipe into **grep**.

Alternatively, you can use synaptic and its search features.

Bonne chance,
~~~ 0;-Dan

---

