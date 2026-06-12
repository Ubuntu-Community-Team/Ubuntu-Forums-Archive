---
title: "Error: Unable to mount ## GB Filesystem"
date: 2009-11-01
forum: Hardware
---

### Post by zeroseven0183 on 2009-11-01
Hi! My friend sent me her 250GB hard drive which is not read in Windows. When mounting it to Ubuntu, I get the following error message:

> 
Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read first NTFS_BLOCK_SIZE bytes of potential restart page.
The file system wasn't safely closed on Windows. Fixing.
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
Failed to sync device /dev/sdb1: Input/output error
Failed to fsync device /dev/sdb1: Input/output error
Failed to close volume /dev/sdb1: Device or resource busy


Now, if I understood it correctly, I need to mount it in Windows (which I do not use).
Is there any way here in Ubuntu to correct this problem?

---

### Post by zeroseven0183 on 2009-11-01
* bump *

---

### Post by zeroseven0183 on 2009-11-05
](*,) * bump *

---

### Post by coffeecat on 2009-11-05
> **zeroseven0183 said:**
> Now, if I understood it correctly, I need to mount it in Windows (which I do not use).
Is there any way here in Ubuntu to correct this problem?

I have good news and bad news.

Install the package 'ntfsprogs' - it's in the Ubuntu repositories. That will install a number of ntfs command line utilities. One of them is ntfsfix. If you run this it might fix the filesystem, but you may also need to run chkdsk from Windows. See 'man ntfsfix':

> ntfsfix  is a utility that fixes some common NTFS problems.  ntfsfix is
       NOT a Linux version of chkdsk.  It only repairs some  fundamental  NTFS
       inconsistencies,  resets  the  NTFS  journal file and schedules an NTFS
       consistency check for the first boot into Windows.

---

### Post by zeroseven0183 on 2009-11-17
Thanks! I never thought of using NTFSProgs for that purpose. Anyway, I also found another disk utility that runs on DOS, it's HDD Regenerator.

I guess the bad news is that I would still have to run chkdsk in Windows. Right?

I appreciate your response.

---

### Post by coffeecat on 2009-11-17
> **zeroseven0183 said:**
> Anyway, I also found another disk utility that runs on DOS, it's HDD Regenerator.

The HDD Regenerator that I found on a google search was for repairing "physically damaged hard drives" by restoring bad sectors - allegedly - and costs $39.99. Which sounds like 40 dollars' worth of snake-oil to me. :-s 

Even if it did work, repairing physical damage is different from repairing a filesystem. So, yes, you may still need chkdsk. :wink:

---

### Post by zeroseven0183 on 2010-02-07
I installed ntfsprogs and was running ntfsfix. However, I get this message:

```
~$ ntfsfix /dev/sdc5
Mounting volume... Error opening partition device: Permission denied.
Failed to startup volume: Permission denied.
FAILED
Attempting to correct errors... Error opening partition device: Permission denied.
FAILED
Failed to startup volume: Permission denied.
Volume is corrupt. You should run chkdsk.
```

I guess I really have to run chkdsk. :frown:

---

### Post by zeroseven0183 on 2010-02-08
Even if I use **sudo** with **ntfsfix**, still the same error. My friend doesn't want to wipe out the hard drive as it contains lot of data.

Although I'm thinking of doing that without her knowing then try recovering the data afterwards.

---

### Post by coffeecat on 2010-02-09
> **zeroseven0183 said:**
> Although I'm thinking of doing that without her knowing then try recovering the data afterwards.

If you mean reformat and then running something like testdisk/photorec, I don't think that's a good idea. Even if photorec does recover all the files, it doesn't recover the original filenames. You get a mass of obscurely-named files in equally obscurely-named folders.

Is there a problem in running chkdsk? Couldn't your friend do it from her Windows system?

---

### Post by zeroseven0183 on 2010-02-09
Yup that's one thing I thought of that I'll get several files without their proper filenames.

> Couldn't your friend do it from her Windows system?

I'll help her help herself. Thanks for reminding!

---

