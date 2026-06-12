---
title: "cdrdao problems"
date: 2007-09-24
forum: Hardware &amp; Laptops
---

### Post by valkarin on 2007-09-24
I am trying to back up my old Play Station games.  I have managed to rip them successfully with cdrdao.  The resulting images play fine in ePSXe.  However, when I try to burn them with cdrdao I get the following error:

```
sudo cdrdao write --eject --speed 4 --device /dev/
hdd --driver generic-mmc /home/valkarin/pSX/cdimages/resident_evil/resident_evi
l.toc
Password:
Cdrdao version 1.2.1 - (C) Andreas Mueller <andreas@daneb.de>
  SCSI interface library - (C) Joerg Schilling
  Paranoia DAE library - (C) Monty

Check http://cdrdao.sourceforge.net/drives.html#dt for current driver tables.

Using libscg version 'ubuntu-0.8ubuntu1'

/dev/hdd: LITE-ON DVDRW LH-20A1P	Rev: KL0A
Using driver: Generic SCSI-3/MMC - Version 2.0 (options 0x0000)

Starting write at speed 16...
Pausing 10 seconds - hit CTRL-C to abort.
Process can be aborted with QUIT signal (usually CTRL-\).
Turning BURN-Proof on
Enabling JustSpeed.
Executing power calibration...
Power calibration successful.
cdrdao: Success.  : scsi sendcmd: no error
CDB:  2A 00 FF FF FF 6A 00 00 1A 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 64 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x64 Qual 0x00 (illegal mode for this track) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 60736
cmd finished after 0.015s timeout 180s
ERROR: Write data failed.
ERROR: Writing failed.

```

Is this a hardware issue?  I am using a LITE-ON DVD Writer LH-20A1P33C.  It is EIDE.  Or am I not doing something write with cdrdao?

---

