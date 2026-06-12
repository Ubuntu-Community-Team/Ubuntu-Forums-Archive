---
title: "SCSI Backup"
date: 2007-03-13
forum: Hardware &amp; Laptops
---

### Post by mcoste on 2007-03-13
Hallo there enthusiasts of the Ubuntu distro.

I have encounterd a very serious problem for some time now...
I have used tor some time a HP DAT backup device, but as my data got bigger and bigger 
i was forced to move on to something bigger. 
I now use a TRANSTEC Backup Changer, this is a device with more tapes, bla bla bla...u know the drill..
The thing is that i had to switch from mt to mtx cause, this is what changers need to controll the device.
So i made a script , which does just this..I`ll post only the essential :

echo DUMP / >> $logfile
/sbin/dump -0a -L ROOT -f /dev/sg0 / >> $logfile 2>&1

So, this uses dump to dump / to the device sg0 .

This is what my device is telling me : 

root@linuxtest:~#  mtx -f /dev/sg0 status
  Storage Changer /dev/sg0:1 Drives, 8 Slots ( 0 Import/Export )
Data Transfer Element 0:Empty
      Storage Element 1:Full
      Storage Element 2:Empty
      Storage Element 3:Empty
      Storage Element 4:Empty
      Storage Element 5:Empty
      Storage Element 6:Empty
      Storage Element 7:Empty
      Storage Element 8:Empty
root@linuxtest:~#

SO, you see he recons that there is a tape in the 1st slot, where he she dump his data.
Well, all nice untill now, but when i execute the dump script, or the command...the following things come up :
1. Kernel errors :

[42950634.740000] sg_write: data in/out 1173774547/65494 bytes for SCSI command 0x0--guessing data in;
[42950634.740000]    program dump not setting count and/or reply_len properly
[42950861.630000] sg_write: data in/out 1173774547/65494 bytes for SCSI command 0x0--guessing data in;
[42950861.630000]    program dump not setting count and/or reply_len properly
[42951529.040000] sg_write: data in/out 1173775461/65494 bytes for SCSI command 0x0--guessing data in;
[42951529.040000]    program dump not setting count and/or reply_len properly
root@linuxtest:~#

2. Script errors :

DUMP: Date of this level 0 dump: Mon Mar 12 09:27:25 2007
  DUMP: Dumping /dev/hda1 (/) to /dev/sg0
  DUMP: Label: ROOT
  DUMP: Writing 64 Kilobyte records
  DUMP: mapping (Pass I) [regular files]
  DUMP: Interrupt received.
  DUMP: Do you want to abort dump?: ("yes" or "no")   DUMP: "Yes" or "No"?
  DUMP: Do you want to abort dump?: ("yes" or "no")   DUMP: "Yes" or "No"?
  DUMP: Do you want to abort dump?: ("yes" or "no")   DUMP: Date of this level 0 dump: Mon Mar 12 09:29:25 2007
  DUMP: Dumping /dev/hda1 (/) to /dev/sg0
  DUMP: Label: ROOT
  DUMP: Writing 64 Kilobyte records
  DUMP: mapping (Pass I) [regular files]
  DUMP: mapping (Pass II) [directories]
  DUMP: estimated 2218775 blocks.
  DUMP: Volume 1 started with block 1 at: Mon Mar 12 09:29:43 2007
  DUMP: write error 128 blocks into volume 1: Cannot allocate memory
  DUMP: Do you want to rewrite this volume?: ("yes" or "no")   DUMP: Interrupt received.
  DUMP: Do you want to abort dump?: ("yes" or "no")


So, guys if any of you have a suggestion, or something..please let me know because i`m out off ideas...
If you need anything else posted, let me know...
Thanks in advance.

Mircea Coste
mircha.net

:( :( :(

---

