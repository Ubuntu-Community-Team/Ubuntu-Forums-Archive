---
title: "HOWTO update KLN-89b IFR GPS database"
date: 2010-06-06
forum: Hardware
---

### Post by heliboy on 2010-06-06
Can't image many folks will be interested in this, but, just in case:

Honeywell/Allied Signal/King/Wingman get the database for the King KLN-89b from Jeppesen, and Jeppesen knows nothing about anything but the Microsoft Corporation.  Under Ubuntu 9.10, kernel 2.6.31-22-generic, wine1.2, on an IBM Thinkpad 600E using the conventional 9-pin serial port, neither the GUI-based AlternativeSetup17.exe, nor the MSDOS-based NETLOAD.EXE, run under wine - they start OK, but they hang. I've fussed extensively with wine's configuration, but no joy.  (I have another application that uses the serial port running fine under wine, so the serial port would seem to be configured correctly.)  dosbox 0.73 (from Synaptic), however, runs NETLOAD.EXE fine.  So I have a nice, IFR-legal, updated GPS, without sending a nickel to Microsoft.  Hurrah!

dosemu also does not run NETLOAD.EXE in my hands - no communication with the GPS takes place.  With dosbox, use of the Ctrl-F8 or Ctrl-F12 speed-up features also causes execution of NETLOAD.EXE to fail.  NETLOAD's handling of serial communications seems unconventional.

---

