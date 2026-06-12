---
title: "My Book Read Errors"
date: 2008-11-24
forum: General Help
---

### Post by ah_skeet on 2008-11-24
I have a WD My Book 750GB Studio Edition with a 550 GB FAT32 partition and a 150 GB HFS+ Time Machine partion (since this was on a Mac). It worked fine for a while, wrote about 200GB to the FAT32 partition, and everything was working fine. 

Now, directory listings in nautilus is incredibly slow causing nautilus to hang for a while. Copying files works quickly, until it'll hit some file, which will casue it to hang for a while, then give an error saying it can't be read.

In gparted, for the FAT32 partition, it gives the warning:
```
Unable to read the contents of this filesystem! Because of this some operations may be unavailable
```

Running fsck.vfat, I get:
```
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Got 48398336 bytes instead of 148303680 at 16384
```

Trying to watch videos via totem, sometimes, it will freeze, then exit with the error "Resource not ready".

Moving files on it takes a about 30 seconds to move a single folder with 2 files in it.

Windows won't mount the drive.

I have another, older, My Book and a FreeAgent both plugged in working fine

Is there a way to repair this? Should I try reformatting it? Will that fix it? (I'm currently copying the data on it over to another drive) Any idea on what the problem is?

---

