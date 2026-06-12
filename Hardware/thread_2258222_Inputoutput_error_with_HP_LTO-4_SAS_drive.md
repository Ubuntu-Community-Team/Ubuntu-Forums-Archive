---
title: "Input/output error with HP LTO-4 SAS drive"
date: 2014-12-25
forum: Hardware
---

### Post by Per_Johansson on 2014-12-25
I'm seeking advice how to troubleshoot this further...

  I have a Adaptec ASC-1405 SAS card and a HP LTO-4 tape drive.

  I make a normal tar backup, tar -cvf /dev/nst0 ... This works with any fuzz.

  But when trying to look at the tape with tar -tvf /dev/nst0 I get  read error (I/O fault). This seems to happen on random places. Two successive runs will not stop  on the same file. When this happens, the tape stops, and tar freezes.  Then after a while (several minutes) the error appears and the tape  starts running again.
  Any ideas?
  I have successfully upgraded firmware and run all tests on the backup  drive on the same hardware, just booting from a Windows 7 disk.
  output from tar: 
tar: /dev/nst0: Cannot read: Input/output error 
tar: /dev/nst0: Cannot read: Input/output error 
tar: Skipping to next header 
tar: /dev/nst0: Cannot read: Input/output error 
tar: /dev/nst0: Cannot read: Input/output error 
tar: Skipping to next header 
tar: A lone zero block at 33363361 
tar: Exiting with failure status due to previous errors

  [HR][/HR]  mt -f /dev/nst0 status SCSI 2 tape drive: File number=0, block number=0, partition=0. Tape block size 0 bytes. Density code 0x46 (LTO-4). Soft error count since last status=0 General status bits on (41010000):  BOT ONLINE IM_REP_EN

  [HR][/HR]  lspci ... Serial Attached SCSI controller: Adaptec ASC-1405 Unified Serial HBA (rev 02)

  [HR][/HR]  uname -a Linux host 3.13.0-43-generic #72-Ubuntu SMP Mon Dec 8 19:35:44 UTC 2014 i686 i686 i686 GNU/Linux

---

