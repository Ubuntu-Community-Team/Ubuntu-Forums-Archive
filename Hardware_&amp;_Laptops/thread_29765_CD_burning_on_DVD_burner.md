---
title: "CD burning on DVD burner"
date: 2005-04-25
forum: Hardware &amp; Laptops
---

### Post by brianglass on 2005-04-25
I just installed a new Pacific Digital double layer DVD burner that for the most part works great. I've burned DVD+R's (single layer), watched movies, etc. However,  I cannot burn a CD-R. I get the following error from Nautilus when trying to burn to a Verbatim 700MB CD-R. I've also tried a 700MB TDK CD-RW without success.

I'm going to try and get my old CD burner installed in another bay and see if I can get it working that way, but it would be really nice to be able to do this. Can anyone help?

```
cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.
cdrecord: fifo had 64 puts and 0 gets.
cdrecord: OPC failed.
cmd finished after 0.886s timeout 60s
Sense flags: Blk 0 (not valid) 
Sense Code: 0x09 Qual 0x00 (track following error) Fru 0x0
Sense Key: 0x4 Hardware Error, Segment 0
Sense Bytes: 70 00 04 00 00 00 00 12 00 00 00 00 09 00 00 00
status: 0x2 (CHECK CONDITION)
CDB:  54 01 00 00 00 00 00 00 00 00
cdrecord: Success. send opc: scsi sendcmd: no error
cdrecord: WARNING: This causes a high risk for buffer underruns.
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
SCSI buffer size: 64512
cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
Linux sg driver version: 3.5.27
Warning: Open by 'devname' is unintentional and not supported.
scsibus: -2 target: -2 lun: -2
devname: '/dev/hdd'
scsidev: '/dev/hdd'
cdrecord: WARNING: This causes a high risk for buffer underruns.
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: Warning: Running on Linux-2.6.10-5-k7
cdrecord: Continuing in 5 seconds...
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Asuming -tao mode.
cdrecord: No write mode specified.
```

---

### Post by xodeus on 2005-04-30
[QUOTE=brianglass]I just installed a new Pacific Digital double layer DVD burner that for the most part works great. I've burned DVD+R's (single layer), watched movies, etc. However,  I cannot burn a CD-R. I get the following error from Nautilus when trying to burn to a Verbatim 700MB CD-R. I've also tried a 700MB TDK CD-RW without success.

I'm going to try and get my old CD burner installed in another bay and see if I can get it working that way, but it would be really nice to be able to do this. Can anyone help?

```
cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.
cdrecord: fifo had 64 puts and 0 gets.
cdrecord: OPC failed.
cmd finished after 0.886s timeout 60s
Sense flags: Blk 0 (not valid) 
Sense Code: 0x09 Qual 0x00 (track following error) Fru 0x0
Sense Key: 0x4 Hardware Error, Segment 0
Sense Bytes: 70 00 04 00 00 00 00 12 00 00 00 00 09 00 00 00
status: 0x2 (CHECK CONDITION)
CDB:  54 01 00 00 00 00 00 00 00 00
cdrecord: Success. send opc: scsi sendcmd: no error
cdrecord: WARNING: This causes a high risk for buffer underruns.
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
SCSI buffer size: 64512
cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
Linux sg driver version: 3.5.27
Warning: Open by 'devname' is unintentional and not supported.
scsibus: -2 target: -2 lun: -2
devname: '/dev/hdd'
scsidev: '/dev/hdd'
cdrecord: WARNING: This causes a high risk for buffer underruns.
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: Warning: Running on Linux-2.6.10-5-k7
cdrecord: Continuing in 5 seconds...
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Asuming -tao mode.
cdrecord: No write mode specified.
```[/QUOTE]
 have you tried with Gnomebaker??
[http://www.ubuntuguide.org/#gnomebaker](http://www.ubuntuguide.org/#gnomebaker)

---

