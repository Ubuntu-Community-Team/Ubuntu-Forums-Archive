---
title: "Rollback rx or any recory system"
date: 2008-11-10
forum: General Help
---

### Post by jv13613 on 2008-11-10
Hi,
  i had an old computer that had some gateway recovery sowtware on it. The kind that boots up before windows. When I went to resize the windows partion the windows file system became corrupted. On a newer computer I have rollback rx. Will this effect wubi and corrupt my system? :confused::(

---

### Post by Orlsend on 2008-11-10
I dont think it would corrupt your virtual drives, I just they may not be at the same point you wan them.

You could back them up and then plug them back in once the restore is done.

---

### Post by jv13613 on 2008-11-11
No,
  I am wondering if wubi will mess up my mbr.
From wikipedia about rollback rx:

 RollBack Rx installs to the hard drive's master boot record, which loads prior to the Windows operating system, which allows the hard drive to be reverted to a previous snapshotted state even in the event that Windows is unable to boot. The user can also elect to revert to a snapshot from within Windows, which requires a reboot or logoff to take effect.

---

### Post by ago on 2008-11-11
Don't that system but should be ok

---

### Post by erdalronahi on 2009-04-04
Definitely do not try that!

I did it on one computer, and the result was desaster. The changes that Wubi did to the MBR made Rollback RX reset everything to the very first snapshot, which is called the "baseline". As a result, all data on that computer was lost.

---

