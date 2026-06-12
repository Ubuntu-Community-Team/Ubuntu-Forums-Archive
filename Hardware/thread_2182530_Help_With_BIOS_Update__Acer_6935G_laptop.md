---
title: "Help With BIOS Update / Acer 6935G laptop"
date: 2013-10-21
forum: Hardware
---

### Post by ScousaJAY on 2013-10-21
hey, 

I have an Acer 6935G that i have an issue with and my last option is to try a BIOS update.

I have been trying to restore the laptop to factory defaults with the restore CD's, but it keeps failing.  i have done a hardware inspection and a few tests on the hard drive and RAM and have found no issues.

Its also worth mentioning that acer have tested the Restore CD's and found them to be working, and so have sent them back to me.

The current BIOS version is 1.10, and the updated version is 1.20, but currently there is no operating system on the computer and i am only able to run linux from a USB drive.

I have downloaded the updated BIOS from the acer support site and there is an option for a DOS update, and a Windows update, and im not sure which one, if any, i could use through Linux.

If anyone could give me some pointers it would be much appreciated.

Thanks

---

### Post by Yellow Pasque on 2013-10-22
google 'freedos' for a suitable environment to use the DOS update.

---

### Post by Mark Phelps on 2013-10-22
> my last option is to try a BIOS update.

Doing a BIOS update rarely helps, unless there is a specific hardware problem the update fixes.  It's not like doing a driver update.

BEFORE you do such an update, be sure BOTH of the following are true:
1) You have a way to save off the current working BIOS to a medium that can be read without a working OS
2) You have a way to restore that saved BIOS, in the event that the update goes badly, without a working OS.

If these are not true, you're risking "bricking" your machine attempting a BIOS update.

---

