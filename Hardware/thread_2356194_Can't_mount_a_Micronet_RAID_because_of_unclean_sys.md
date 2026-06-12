---
title: "Can't mount a Micronet RAID because of unclean system?"
date: 2017-03-20
forum: Hardware
---

### Post by huffmanp on 2017-03-20
I have a couple old Micronet RAID units that connect with a wide SCSI cable and an Adaptec 29160 card that served me well for many years.  Unfortunately when I moved to Windows 10, I couldn't find a compatible driver fro the 29160.  I just thought, "Oh well, I got my important files backed off the RAID and I have a 29160 in my Ubuntu machine, so I'll be fine."  Well, now I'm looking for a lost zip file, and I thought I better look on the old RAID.  The ubuntu machine has RAID #2 plugged into it and worked fine.  Except today I started looking into it and the RAID didn't appear. "Damn upgrades", I was thinking, until I looked at the back and found the SCSI cable was unplugged. Back in business.  I switched in RAID #1 from my previous windows machine, and booted up.  The 29160 searches and finds the SCSI ID and the RAID #1 shows up in the file explorer,  but when I try to open it, I get a error message: "Error mounting /dev/sdb1 at /media/paul/RAID: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000" "/dev/sdb1" "/media/paul/RAID"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sdb1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option."

I thought I could get this to work read only by going to terminal and typing: 'sudo mount -t "ntfs" -o ro "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000" "/dev/sdb1" "/media/paul/RAID"'
but I don't seem to have the syntax correct.  Am I close?

---

### Post by alexandari on 2017-03-21
You can clean a dirty ntfs partition using this command:

```
 ntfsfix -d /dev/sdaX 
```

assuming you have the ntfs-3g package

Then try to mount again

---

### Post by huffmanp on 2017-03-21
Thanks that worked.  But I didn't find the lost zip files.  

> sudo ntfsfix -d /dev/sdb1
[sudo] password for paul: 
Mounting volume... The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
Checking the alternate boot sector... OK
NTFS volume version is 3.1.
NTFS partition /dev/sdb1 was processed successfully.

---

