---
title: "HP DDS tape drive C5683A"
date: 2012-10-12
forum: Hardware
---

### Post by leo1234 on 2012-10-12
Hello,

Since a few years I am exploring ubuntu. My next step is up to now not successful.

PC:
Intel i5-2500 with an ultra scsi card Sym 8750SP with chip SYM53C875.
Connected to this card is an HP ScanJet 5P; the scanner works well, so the scsi card is correctly recognized and functioning.

Also connected is a DDS HP tape drive C5683A, which I need for backup. 
This tape drive is not seen. "mt -f /dev/st0" results in "unknown file or directory" while there is a tape in the drive.

Do I need a special driver? And if so, where can I find it?

Do I need a kernel module for the tape drive? And if so, where can I find it?

Under OS/2 all hardware functions as it should: I use a multi-boot system.

Please can anyone give me a hint what I should do so that I can backup my data to tape?

---

### Post by leo1234 on 2012-10-29
Solved; loaded kernel module st.

---

