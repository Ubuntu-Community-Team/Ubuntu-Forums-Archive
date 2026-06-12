---
title: "Error mounting Sandisk Cruzer USB drive"
date: 2008-09-27
forum: Hardware
---

### Post by MightyFrog on 2008-09-27
When I inserted my 8 GB Sandisk Cruzer USB drive, I got an error message that the drive failed to mount. I poked around a little on the forums to find the terminal commands to try mounting it. Here's the output of those commands.

```
globalnet@globalnet-desktop1:~$ sudo mkdir /mnt/usb
globalnet@globalnet-desktop1:~$ sudo mount /dev/sdb1 /mnt/usb
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

```

I've certainly not tried to implement any RAID-like things on the drive. I have reformatted the drive since I bought it--it's one big NTFS partition. The drive works fine in Windows. Can anyone tell me what's going on? Thanks.

---

### Post by vanadium on 2008-09-27
Your file system was not properly closed (for example removed USB from Windows without the "safely remove hardware" icon). What you need to do is very clearly indicated in the error message. Obviously, you are in the first case, since this is not a raid.

> run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important!
I can't say it in better English myself.

---

### Post by MightyFrog on 2008-09-27
OK, I'll try that. I wasn't trying to be dense, but I wasn't thinking the problem would actually be with the disk itself--it works fine in Windows, as I said.

---

### Post by jpeery on 2008-09-27
I'm curious, what does chkdsk do?  Seems there should be a way to set/reset the flag that it was removed without closing.  Just curious, perhaps it's just easier to do in Windows.  I'm just thinking if that happened to me I'd be out of luck since I don't have, use or touch a Windows system.  I'd have to go load it on something to do this.  I guess at the end of the day I'd probably not have an NTFS stick.  However, say someone gave me one, isn't there a way around the Windows chkdsk requirement?  Perhaps WINE and chkdsk?
Thanks, interesting thread,
Jason

---

### Post by vanadium on 2008-09-27
chkdsk does check the integrity of the file system. It checks if everything is consistent.

There is certainly a way around chkdsk, exept if you have an ntfs formatted partition. In linux, you can use the fsck command: I explained this also here: [http://ubuntuforums.org/showpost.php?p=5864923&postcount=2](http://ubuntuforums.org/showpost.php?p=5864923&postcount=2)

ntfs is a complex format and it is proprietary: this is why you need MS Windows to check/repair such a system with 100% reliability. (I guess the linux ntfsfix command can also help to a significant extent. However, it is not guaranteed and I do not have experience)

---

