---
title: "i cannot get lubuntu to run any dvd disks. cd disks work fine"
date: 2020-02-29
forum: Hardware
---

### Post by toxasax on 2020-02-29
i have dvd/cd drive and any dvd is not working while cd disks work 

Here is the outputs of some commands if it needs:

**1) sudo wodim --devices**

wodim: Overview of accessible drives (2 found) :
-------------------------------------------------------------------------
 0  dev='/dev/sg1'      rwrw-- : 'TSSTcorp' 'CDDVDW SH-S223C'
 1  dev='/dev/sg2'      rwrw-- : 'CWID' 'USB SCSI CD-ROM'


**2) sudo cdrskin --devices**

cdrskin 1.5.0 : limited cdrecord compatibility wrapper for libburn
cdrskin: scanning for devices ...
cdrskin: SORRY : Cannot open busy device '/dev/sr1'
cdrskin: ( Most recent system error: 16  'Device or resource busy' )
cdrskin: NOTE : Failed to open device '/dev/sr11'
cdrskin: ( Most recent system error: 6  'No such device or address' )
cdrskin: NOTE : Failed to open device '/dev/sr12'
cdrskin: ( Most recent system error: 6  'No such device or address' )
cdrskin: SORRY : Cannot open busy device '/dev/sr1'
cdrskin: ( Most recent system error: 16  'Device or resource busy' )
cdrskin: ... scanning for devices done
cdrskin: Overview of accessible drives (1 found) :
-----------------------------------------------------------------------------
0  dev='/dev/sr0'  rwrw-- :  'TSSTcorp'  'CDDVDW SH-S223C'


**3) sudo xorriso -devices**

xorriso 1.5.0 : RockRidge filesystem manipulator, libburnia project.

Beginning to scan for devices ...
libburn : SORRY : Cannot open busy device '/dev/sr1' : Device or resource busy
libburn : NOTE : Failed to open device '/dev/sr11' : No such device or address
libburn : NOTE : Failed to open device '/dev/sr12' : No such device or address
libburn : SORRY : Cannot open busy device '/dev/sr1' : Device or resource busy
Full drive scan done
-----------------------------------------------------------------------------
0  -dev '/dev/sr0' rwrw-- :  'TSSTcorp' 'CDDVDW SH-S223C' 
-----------------------------------------------------------------------------
xorriso : NOTE : Tolerated problem event of severity 'SORRY'
xorriso : NOTE : -return_with SORRY 32 triggered by problem severity SORRY



Please help

---

### Post by CelticWarrior on 2020-02-29
A different laser is used for CDs and DVDs. It's possible one being defective while the other still works.

---

