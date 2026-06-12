---
title: "what does this error code mean?"
date: 2008-08-17
forum: General Help
---

### Post by harryliddic on 2008-08-17
this is the error code I received when running dvdauthor to burn a DVD I am having a tough time deciphering it. Can anyone help?> DVDAuthor::dvdauthor, version 0.6.14.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>

INFO: Locale=en_US.UTF-8
INFO: Converting filenames to UTF-8
INFO: dvdauthor creating table of contents
ERR:  No .IFO files to process
Executing 'genisoimage -dvd-video /home/harry/Videos/ | builtin_dd of=/dev/dvd obs=32k seek=0'
I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage: Argument list too long. Failed to read VIDEO_TS.IFO
genisoimage: Can't open VMG info for '/home/harry/Videos/'.
genisoimage: Unable to parse DVD-Video structures.
genisoimage: Could not find correct 'VIDEO_TS' directory.
genisoimage: Unable to make a DVD-Video image.
Possible reasons:
  - VIDEO_TS subdirectory was not found on specified location
  - VIDEO_TS has invalid contents
:-( write failed: Input/output error
* BD/DVDÂ±RW/-RAM format utility by <appro@fy.chalmers.se>, version 7.0.
:-( unable to open("/dev/srcd0"): No such file or directory
I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage: Argument list too long. Failed to read VIDEO_TS.IFO
genisoimage: Can't open VMG info for '/home/harry/Videos/'.
genisoimage: Unable to parse DVD-Video structures.
genisoimage: Could not find correct 'VIDEO_TS' directory.
genisoimage: Unable to make a DVD-Video image.
Possible reasons:
  - VIDEO_TS subdirectory was not found on specified location
  - VIDEO_TS has invalid contents
dvdrecord: Cannot allocate memory. WARNING: Cannot do mlockall(2).
dvdrecord: WARNING: This causes a high risk for buffer underruns.
dvdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
dvdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
dvdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '0,0,0'
scsibus: 0 target: 0 lun: 0
Linux sg driver version: 3.5.34
dvdrecord: Warning: using inofficial version of libscg (bero-0.5a '@(#)scsitransp.c	1.81 01/04/20 Copyright 1988,1995,2000 J. Schilling').
dvdrecord: Sorry, no CD/DVD-Drive found on this target.
dvdrtools v0.3.1
Portions (C) 2002-2006 Ark Linux <bero@arklinux.org>
This program is free software; you can redistribute it and/or modify it under
the terms of the GNU General Public License as published by the Free Software
Foundation; either version 2, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY
WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR
A PARTICULAR PURPOSE.  See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with
this program; see the file COPYING.  If not, write to the Free Software
Foundation, 59 Temple Place, Suite 330, Boston, MA 02111-1307, USA.
Based on:
Cdrecord 1.11a15 (i486-pc-linux-gnu) Copyright (C) 1995-2001 Jörg Schilling
Using libscg version 'bero-0.5a'
Device type    : Disk
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'ATA     '
Identifikation : 'WDC WD800BB-56JK'
Revision       : '05.0'
Device seems to be: Generic CCS Disk.


---

