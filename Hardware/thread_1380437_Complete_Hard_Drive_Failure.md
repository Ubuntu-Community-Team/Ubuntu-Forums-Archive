---
title: "Complete Hard Drive Failure"
date: 2010-01-13
forum: Hardware
---

### Post by kogger on 2010-01-13
Yesterday I was using my laptop when it crashed, so I did a hard reboot. When it got to Grub it displayed "Grub loading.", and then did nothing after that. After trying to reboot again the new message became "Grub loadingRead Error", with "Read Error" appearing several seconds after "Grub  loading". Then, after a little while, it changed back to "Grub loading." but then began showing messages such as "unknown command 'if'", displaying a few and then displaying seemingly blank messages to create a blank screen.

Now, thanks to the live cd's disk utility, I can confirm that my hard drive is failing. But I had already tried to back some things up from one partition to my primary data (and backup) partition, as I had originally assumed it was just a software issue and that a re-install would fix it. But apparently, writing to a failing disk causes it to screw up more, and so now I'm left with a failing hard drive whose only accessible partitions are exactly the ones that don't have my data on them. Attempting to mount my data partition (whose filesystem is ntfs) in a live cd session results in an error:

```
Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read vcn 0x1: Input/output error
Failed to mount '/dev/sda3': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
```

Is there any way to access the partition and get some of my files back?

---

### Post by IcarusR on 2010-01-13
Photorec [http://www.cgsecurity.org/wiki/PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec")
Testdisk [http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")

Both may be of help.
I would suggest making a copy of the drive (using a clone program) first be fore trying anything, so if it gets messed up even more you still have the copy.
Best to take drive out of laptop & connect it to a desktop.

---

