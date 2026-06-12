---
title: "Cannot burn cd's :'("
date: 2005-01-24
forum: Hardware &amp; Laptops
---

### Post by crypticreign on 2005-01-24
xcdroast and graveman say they could not find a cd burner device...

root@hell:~ # cdrecord dev=/dev/hdc -scanbus
Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.10-2-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Using libscg version 'ubuntu-0.8ubuntu1'.
cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
scsibus1:
        1,0,0   100) 'HP      ' 'CD-Writer+ 9300 ' '1.0c' Removable CD-ROM
        1,1,0   101) *
        1,2,0   102) *
        1,3,0   103) *
        1,4,0   104) *
        1,5,0   105) *
        1,6,0   106) *
        1,7,0   107) *

my /etc/default/cdrecord file

#ident @(#)cdrecord.dfl 1.4 02/07/07 Copyr 1998 J. Schilling
#
# This file is /etc/default/cdrecord
# It contains defaults that are used if no command line option
# or environment is present.
#
# The default device, if not specified elswhere
#
CDR_DEVICE=hp

#
# The default speed, if not specified elswhere
#
# Note that newer cdrecord versions do not default
# to speed=1. For MMC compliant drives, the default
# is to write at maximum speed, so it in general does
# not make sense to set up a default speed in /etc/default/cdrecord
#
#CDR_SPEED=40

#
# The default FIFO size if, not specified elswhere
#
CDR_FIFOSIZE=4m

#
# The following definitions allow abstract device names.
# They are used if the device name does not contain the
# the characters ',', ':', '/' and '@'
#
# Unless you have a good reason, use speed == -1 and let
# cdrecord use it's intercal drive specific defaults.
#
# drive name    device  speed   fifosize driveropts
#
teac=           1,3,0   -1      -1      ""
panasonic=      1,4,0   -1      -1      ""
plextor=        1,4,0   -1      -1      ""
sanyo=          1,4,0   -1      -1      burnfree
yamaha=         1,5,0   -1      -1      ""
cdrom=          0,6,0   2       1m      ""
hp=             ATAPI:1,0,0    -1      -1      ""

this is Linux 2.6.10-2-386  with an HP 9300 burner.. this is the first distro to not recognize my cd burner (ive used redhat, fedora, debian, lunar)

---

