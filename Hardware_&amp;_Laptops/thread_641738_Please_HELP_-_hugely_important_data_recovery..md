---
title: "Please HELP - hugely important data recovery."
date: 2007-12-15
forum: Hardware &amp; Laptops
---

### Post by jayhay548 on 2007-12-15
Hi everyone - I'm very new to ubuntu and desparate for some help.

I've idiotically gone too long without backing up some very important data regarding unrepeatable medical studies and the other day my hard drives which are 2 x 100GB in a RAID arrangement in a Toshiba Qosmio laptop crashed.

I get the error message file not found or corrupt: HAL.DLL

I am running ubuntu from the CD and am trying to access the hard drive(s) but ubuntu is giving me the error:

Cannot mount volume:

$MFT has invalid magic. Failed to load $MFT: input/output error Failed to mount 'dev/sda1': input/output error NTFS is either inconsistent or you have hardware faults, or you have a softRAID/fakeRAID hardware. In the first case run chkdsk /f on Windows the reboot TWICE.  If you have softRAID/fakeRAID then first you must activate it and mount a different device under the /dev/mapper/directory. Please see the 'dmraid' documentation for more details.


Please can somebody help me. I'm fairly computer literate but LINUX/ubuntu is new to me so go easy.


Thanks

James

---

### Post by Sef on 2007-12-15
1) Do not boot up that computer unless it is with a Live CD.

2) Try [Knoppix]("http://knoppix.com"), it is the best at this type of recovery.  I have used it to pull off files off of computers that did not boot up.

3) If that fails, then take it in to a data recovery center and pay them the money to recover what they can.

---

### Post by stickmangumby on 2007-12-15
What kind of RAID are you running? If it's not RAID0, you should be fine - don't panic yet :)

---

