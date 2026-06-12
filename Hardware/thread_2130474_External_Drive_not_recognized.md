---
title: "External Drive not recognized"
date: 2013-03-29
forum: Hardware
---

### Post by redenex on 2013-03-29
I get this following error thrown when I connect the external drive:

[IMG]http://img11.imageshack.us/img11/6139/screenshotfrom201303292.png[/IMG]



Help please?

---

### Post by sudodus on 2013-03-29
Well, do you have a raid system? If not,

check in Windows with ```
chkdsk /f
``` or in newer Windows versions use the GUI frontend to check your disk (drive or volume).

You can also check the S.M.A.R.T. status in the BIOS menu system or with the software ***smartctl***

---

### Post by redenex on 2013-03-29
Oh okay, I have Windoze 8 on the system.


Is there anything we can do from Ubuntu itself?

---

### Post by sudodus on 2013-03-29
Ubuntu itself suggests chkdsk /f and I think many of us at the Ubuntu Forums do it too. There is no free software tool that can compete with Microsoft's own tool to check and repair Microsoft's file systems.

But we can use a linux file system instead of NTFS ;-)

---

### Post by redenex on 2013-03-29
:) Thanks, shall check it out.

---

### Post by redenex on 2013-03-29
I have a feeling, there is some issue with the connecting cord, maybe loose connection. :)

---

### Post by sudodus on 2013-03-29
That is much better than a corrupted file system :-)

---

### Post by el puma inmundo on 2013-03-29
[h=2]Re: Unable to mount the drive[/h] 		 				 				 					 				 		 			 				[INDENT] 					I have a similar issue.  I am relatively inexperienced with Linux.  I have been using a  Samsung M2 320 GB external hard drive for over a year and a half.  I am  now operating with Ubuntu 12.04 Precise.  Today, I began having problems  mounting the hard drive and receive the following error message:

Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

The computer doesn't have Windows installed, and I don't know what to  make of the error message.  That I know of, the hard drive hasn't  received any trauma recently.  I did install a sizeable update the other  day, but I don't know that that would affect the hard drive's  performance.  Any suggestions?  Thanks. 				
[/INDENT]

---

### Post by redenex on 2013-03-29
Because, when I logged in from Windoze, I could access the files, tried copying to the computer hard disk, and while the process was on, it got disconnected - reconnected - disconnected...... Shall check it out more in detail tomorrow.

---

### Post by el puma inmundo on 2013-03-29
**Re: Unable to mount the drive**

                                                                                                                        [INDENT]                     I have a similar issue.  I am relatively inexperienced with Linux.  I have been using a  Samsung M2 320 GB external hard drive for over a year and a half.  I am  now operating with Ubuntu 12.04 Precise.  Today, I began having problems  mounting the hard drive and receive the following error message:

Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

The computer doesn't have Windows installed, and I don't know what to  make of the error message.  That I know of, the hard drive hasn't  received any trauma recently.  I did install a sizeable update the other  day, but I don't know that that would affect the hard drive's  performance.  Any suggestions?  Thanks.                 
[/INDENT]

---

### Post by Bashing-om on 2013-03-29
@ el puma inmundo'

This "3: ntfs_attr_pread_i: ntfs_pread failed: Input/output error" indicates a Window's format (ntfs) // Same advise from above applies. Take the disk to a windows machine and run the windows' diagnostics on the disk.[INDENT=3]when you have too, you have too

[/INDENT]

---

### Post by sudodus on 2013-03-30
> **Bashing-om said:**
> @ el puma inmundo'

This "3: ntfs_attr_pread_i: ntfs_pread failed: Input/output error" indicates a Window's format (ntfs) // Same advise from above applies. Take the disk to a windows machine and run the windows' diagnostics on the disk.[INDENT=3]when you have too, you have too

[/INDENT]

+1

---

