---
title: "Problem reinstalling previous OS"
date: 2008-09-01
forum: General Help
---

### Post by erod on 2008-09-01
I installed Xubuntu on an old IBM Aptive PIII (2163/580).  I was trying to use the recovery disk that came with the PC to restore it to its factory state (Win 98).  I can't get it to work and I wondering if it had anything to do with my install of Xubuntu. It says something about write protection on drive A, but there is no floppy disk inserted.  The only thing that is running is the recovert CD. I can't do anything after that. Any help would be great.  Thanks. 

The screen shows the following:

Invalid drive specification
Locking operation failed
Invalid drive specification

PKUnzip (R) FAST! Extract Utility Version 2.06 01-24-94
Copyright. 1989-1994 PKWARE Inc. All Rights Reserved.
PKUNZIP Reg. U.S. Pat. and Tm. Off. IBM Licensed Version

Pentium detected.
XMS Version 3.00 detected.

Searching ZIP: G:/RECOVERY/US/APTIVA01.ZIP

Write protect error writing drive A
Abort, Retry, Fail?

---

### Post by ScarySquirrel on 2010-04-23
Have you tried just putting a floppy in there for the hell of it?

---

### Post by oldfred on 2010-04-23
Windows does not like ext partitions. It does not see them. 
You either should reformat drive as FAT (does win98 even work with NTFS?) or zero out drive so it sees new drive.

---

