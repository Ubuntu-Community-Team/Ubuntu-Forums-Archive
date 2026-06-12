---
title: "K3b errors"
date: 2006-08-04
forum: Hardware &amp; Laptops
---

### Post by Im_Just_GrayT on 2006-08-04
I'v been trying to get a cd burnt for a while now. for some reason all the software i try, fails. Here's the output of a failed cd burn with k3b.

Command Line Output:
```
shane@ShaneDeskLinux:~$ k3b
kbuildsycoca running...
shane@ShaneDeskLinux:~$ k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Link points to "/tmp/ksocket-root"
Link points to "/tmp/kde-root"
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kbuildsycoca running...
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Launched ok, pid = 18240
OggS-SEEK: at 0 want 60408 got 51136 (diff-requested 60408)
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x4c00477
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x4c00477
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  18
  Minor opcode:  0
  Resource id:  0x4c00477
OggS-SEEK: at 60352 want 520 got 0 (diff-requested -59832)

```

Debugging output from K3b(after failed burn):
```
System
-----------------------
K3b Version: 0.12.14

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.15-26-386
Devices
-----------------------
HL-DT-ST CD-RW GCE-8400B B104 (/dev/hdd, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM] [CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R]

LITE-ON DVDRW SHW-160P6S PS0A (/dev/hdc, ) at /media/dvdrw0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD-R DL; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-R Dual Layer Sequential; DVD-R Dual Layer Jump; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite; Layer Jump]
Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.15-26-386
/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
/usr/bin/X11/cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
/usr/bin/X11/cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
/usr/bin/X11/cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
Text len: 702
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 0 = CD-DA
Using libscg version 'debian-0.8debian2'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'LITE-ON '
Identifikation : 'DVDRW SHW-160P6S'
Revision       : 'PS0A'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009
Profile: 0x002B 
Profile: 0x001B 
Profile: 0x001A 
Profile: 0x0016 
Profile: 0x0015 
Profile: 0x0014 
Profile: 0x0013 
Profile: 0x0011 
Profile: 0x0010 
Profile: 0x000A 
Profile: 0x0009 (current)
Profile: 0x0008 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE FORCESPEED 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 996864 = 973 KB
FIFO size      : 4194304 = 4096 KB
pregap1: -1
Track 01: audio   33 MB (03:21.49) no preemp swab copy
Track 02: audio   40 MB (04:03.70) no preemp swab copy
Track 03: audio   51 MB (05:07.20) no preemp swab copy
Track 04: audio   40 MB (03:59.57) no preemp swab copy
Track 05: audio   34 MB (03:22.89) no preemp swab copy
Track 06: audio   36 MB (03:37.62) no preemp swab copy
Track 07: audio   44 MB (04:26.82) no preemp swab copy
Track 08: audio   11 MB (01:06.20) no preemp swab copy
Track 09: audio   15 MB (01:32.53) no preemp swab copy
Track 10: audio   45 MB (04:31.81) no preemp swab copy
Track 11: audio   44 MB (04:22.98) no preemp swab copy
Track 12: audio   52 MB (05:09.40) no preemp swab copy
Track 13: audio   56 MB (05:33.48) no preemp swab copy
Total size:      507 MB (50:15.73) = 226180 sectors
Lout start:      507 MB (50:17/55) = 226180 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  ATIP start of lead in:  -11933 (97:22/67)
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 43
Manufacturer: Acer Media Technology, Inc.
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 133669
Forcespeed is OFF.
Starting to write CD/DVD at speed 24 in real SAO mode for single session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Turning BURN-Free on
Performing OPC...
Sending CUE sheet...
/usr/bin/X11/cdrecord: faio_wait_on_buffer for writer timed out.
/usr/bin/X11/cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 FF FF E0 ED 00 02 97 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 30 06 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x06 (cannot format medium - incompatible medium) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63648
cmd finished after 26.038s timeout 200s
/usr/bin/X11/cdrecord: Could not write Lead-in.
59/74)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 43
Manufacturer: Acer Media Technology, Inc.
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 133669
SAO startsec: -11933
Writing lead-in...
write CD-Text data: error after 381888 bytes
Writing  time:  346.281s
BURN-Free was never needed.
/usr/bin/X11/cdrecord: fifo had 64 puts and 0 gets.
/usr/bin/X11/cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=/dev/hdc speed=24 -dao driveropts=burnfree textfile=/tmp/kde-shaneYzIRPS/k3bcdBpsa.dat -eject -useinfo -audio -shorttrack /home/shane/tmp/k3b_audio_1_01.inf /home/shane/tmp/k3b_audio_1_02.inf /home/shane/tmp/k3b_audio_1_03.inf /home/shane/tmp/k3b_audio_1_04.inf /home/shane/tmp/k3b_audio_1_05.inf /home/shane/tmp/k3b_audio_1_06.inf /home/shane/tmp/k3b_audio_1_07.inf /home/shane/tmp/k3b_audio_1_08.inf /home/shane/tmp/k3b_audio_1_09.inf /home/shane/tmp/k3b_audio_1_10.inf /home/shane/tmp/k3b_audio_1_11.inf /home/shane/tmp/k3b_audio_1_12.inf /home/shane/tmp/k3b_audio_1_13.inf 


```

Anyone? Help would be greatly appreciated. Thanks.

---

### Post by patrick295767 on 2006-08-04
> **Im_Just_GrayT said:**
> I'v been trying to get a cd burnt for a while now. for some reason all the software i try, fails. Here's the output of a failed cd burn with k3b.

Command Line Output:
```
shane@ShaneDeskLinux:~$ k3b
kbuildsycoca running...
shane@ShaneDeskLinux:~$ k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Link points to "/tmp/ksocket-root"
Link points to "/tmp/kde-root"
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kbuildsycoca running...
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
kcmshell: ERROR: (K3bDevice::Device) Unable to do inquiry.
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Launched ok, pid = 18240
OggS-SEEK: at 0 want 60408 got 51136 (diff-requested 60408)
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x4c00477
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x4c00477
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  18
  Minor opcode:  0
  Resource id:  0x4c00477
OggS-SEEK: at 60352 want 520 got 0 (diff-requested -59832)

```

Debugging output from K3b(after failed burn):
```
System
-----------------------
K3b Version: 0.12.14

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.15-26-386
Devices
-----------------------
HL-DT-ST CD-RW GCE-8400B B104 (/dev/hdd, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM] [CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R]

LITE-ON DVDRW SHW-160P6S PS0A (/dev/hdc, ) at /media/dvdrw0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD-R DL; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-R Dual Layer Sequential; DVD-R Dual Layer Jump; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite; Layer Jump]
Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.15-26-386
/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
/usr/bin/X11/cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
/usr/bin/X11/cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
/usr/bin/X11/cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
Text len: 702
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 0 = CD-DA
Using libscg version 'debian-0.8debian2'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'LITE-ON '
Identifikation : 'DVDRW SHW-160P6S'
Revision       : 'PS0A'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009
Profile: 0x002B 
Profile: 0x001B 
Profile: 0x001A 
Profile: 0x0016 
Profile: 0x0015 
Profile: 0x0014 
Profile: 0x0013 
Profile: 0x0011 
Profile: 0x0010 
Profile: 0x000A 
Profile: 0x0009 (current)
Profile: 0x0008 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE FORCESPEED 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 996864 = 973 KB
FIFO size      : 4194304 = 4096 KB
pregap1: -1
Track 01: audio   33 MB (03:21.49) no preemp swab copy
Track 02: audio   40 MB (04:03.70) no preemp swab copy
Track 03: audio   51 MB (05:07.20) no preemp swab copy
Track 04: audio   40 MB (03:59.57) no preemp swab copy
Track 05: audio   34 MB (03:22.89) no preemp swab copy
Track 06: audio   36 MB (03:37.62) no preemp swab copy
Track 07: audio   44 MB (04:26.82) no preemp swab copy
Track 08: audio   11 MB (01:06.20) no preemp swab copy
Track 09: audio   15 MB (01:32.53) no preemp swab copy
Track 10: audio   45 MB (04:31.81) no preemp swab copy
Track 11: audio   44 MB (04:22.98) no preemp swab copy
Track 12: audio   52 MB (05:09.40) no preemp swab copy
Track 13: audio   56 MB (05:33.48) no preemp swab copy
Total size:      507 MB (50:15.73) = 226180 sectors
Lout start:      507 MB (50:17/55) = 226180 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  ATIP start of lead in:  -11933 (97:22/67)
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 43
Manufacturer: Acer Media Technology, Inc.
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 133669
Forcespeed is OFF.
Starting to write CD/DVD at speed 24 in real SAO mode for single session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Turning BURN-Free on
Performing OPC...
Sending CUE sheet...
/usr/bin/X11/cdrecord: faio_wait_on_buffer for writer timed out.
/usr/bin/X11/cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 FF FF E0 ED 00 02 97 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 30 06 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x06 (cannot format medium - incompatible medium) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63648
cmd finished after 26.038s timeout 200s
/usr/bin/X11/cdrecord: Could not write Lead-in.
59/74)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 43
Manufacturer: Acer Media Technology, Inc.
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 133669
SAO startsec: -11933
Writing lead-in...
write CD-Text data: error after 381888 bytes
Writing  time:  346.281s
BURN-Free was never needed.
/usr/bin/X11/cdrecord: fifo had 64 puts and 0 gets.
/usr/bin/X11/cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=/dev/hdc speed=24 -dao driveropts=burnfree textfile=/tmp/kde-shaneYzIRPS/k3bcdBpsa.dat -eject -useinfo -audio -shorttrack /home/shane/tmp/k3b_audio_1_01.inf /home/shane/tmp/k3b_audio_1_02.inf /home/shane/tmp/k3b_audio_1_03.inf /home/shane/tmp/k3b_audio_1_04.inf /home/shane/tmp/k3b_audio_1_05.inf /home/shane/tmp/k3b_audio_1_06.inf /home/shane/tmp/k3b_audio_1_07.inf /home/shane/tmp/k3b_audio_1_08.inf /home/shane/tmp/k3b_audio_1_09.inf /home/shane/tmp/k3b_audio_1_10.inf /home/shane/tmp/k3b_audio_1_11.inf /home/shane/tmp/k3b_audio_1_12.inf /home/shane/tmp/k3b_audio_1_13.inf 


```

Anyone? Help would be greatly appreciated. Thanks.

You wanna burn audio ?
 
Try maybe with IGNORE option, that helped me for one shitty burning hardware. ...

---

### Post by Robor on 2006-08-04
Errors here as well.  Device busy?  No, it's not.  :-/

System
-----------------------
K3b Version: 0.12.14

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.15-26-686
Devices
-----------------------
MATSHITA DVD-RAM UJ-822S 1.61 (/dev/hdc, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-RAM; DVD-R; DVD-RW; DVD+R; DVD+RW] [DVD-ROM; DVD-R Sequential; DVD-RAM; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; CD-ROM; CD-R; CD-RW] [SAO; TAO; Restricted Overwrite]

K3b
-----------------------
Size of filesystem calculated: 3570

Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.15-26-686
/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
/usr/bin/X11/cdrecord: Device or resource busy. Cannot open '/dev/hdc'. Cannot open SCSI driver.
/usr/bin/X11/cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
/usr/bin/X11/cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
/usr/bin/X11/cdrecord: 
/usr/bin/X11/cdrecord: For more information, install the cdrtools-doc
/usr/bin/X11/cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 3 = CD-ROM XA mode 2

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=/dev/hdc speed=24 -tao driveropts=burnfree -eject -multi -xa -tsize=3570s - 

mkisofs
-----------------------
3570
INFO: UTF-8 character encoding detected by locale settings.
 Assuming UTF-8 encoded filenames on source filesystem,
 use -input-charset to override.

mkisofs command:
-----------------------
/usr/bin/X11/mkisofs -gui -graft-points -volid Lina's CD -volset  -appid K3B THE CD KREATOR (C) 1998-2005 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-robor007/k3beFIqXb.tmp -rational-rock -hide-list /tmp/kde-robor007/k3bo9cbEa.tmp -joliet -hide-joliet-list /tmp/kde-robor007/k3bt7bzva.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-robor007/k3bhCzZ6b.tmp

---

### Post by Robor on 2006-08-04
Followup on my post above.  I did a 'sudo k3b' and while it produced a spew of errors in the terminal, it worked!  Permissions issue?

---

### Post by Im_Just_GrayT on 2006-08-04
Does anyone know what this means?

```
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed

```

And/Or how to fix it?

---

### Post by Robor on 2006-08-04
> **Im_Just_GrayT said:**
> Does anyone know what this means?

```
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed

```

And/Or how to fix it?
I got that error in the terminal when I ran K3B as 'sudo' but the CD burned just fine.  Did you try running K3B as sudo?

---

### Post by Im_Just_GrayT on 2006-08-04
I'm trying that right now(with the simulate box checked). The drive seems to be working, but the progress bars and the buffer bars show nothing. I also noticed that It chose to burn in RAW mode. Is that a problem?
And if it matters I am burning an audio cd.

Edit:
 It is now hanging at "Starting RAW simulation at 16x speed"
The progress indicator says that it is preparing write process
And all the progress/buffer indicators show 0% or no data.

The thing that confuses me is that the drive is working. The light is blinking, and I can hear it spinning.

---

### Post by patrick295767 on 2006-08-05
> **Robor said:**
> Followup on my post above.  I did a 'sudo k3b' and while it produced a spew of errors in the terminal, it worked!  Permissions issue?
 
For burning, you should be root indeed.
Or you can use K3B SETUP 
to set the permissions / groups ... and so on 

Cheers

---

### Post by Im_Just_GrayT on 2006-08-05
I dont know why, but its just running Extremely slow. Finally one of the buffer bars shows something (FIFO 85%) but thats the only one. This time I'm burning a dvd, and again, the drive seems to be working(lights, sound, etc...). I just dont understand why. Its a brand new burner, I'm running it as root(sudo) but the status shows nothing.  Any more ideas?

edit: While searching for possible solutions I found something about detecting dvd drives and stuff. I tried "dmesg | grep dvd" and it shows nothing. apparently ubuntu thinks my dvd drive is a cdrom.

---

