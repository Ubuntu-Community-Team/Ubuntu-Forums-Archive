---
title: "IDE drive (Windows-formatted) not detected or not accessible"
date: 2008-10-27
forum: Hardware
---

### Post by sgcharest on 2008-10-27
Running Ubuntu 8.04 loaded on an 80 gig SATA hard drive already installed and running well for several months.  Connected an older 80 gig IDE drive which was Windows formatted and contains data I should be able to transfer and access to the SATA drive. (After which I will wipe the drive and use it for additional storage).

Connected the IDE drive.  Ubuntu loaded as usual.  Went to "Places" and there does not seem to be any evidence that a second drive is there.  However, there is a new file under "Computer" called "Lost and Found."  I can't access this file (i get error message "You do not have permission to access this file"), and there doesn't seem to be any other listing of what might be on the file.

My understanding is that Ubuntu should at least be able to read the partitions in the drive and access those files for which I have apps (e.g., OpenOffice for .doc files, Amarok for .mp3 files, etc.)

Two questions:

1)  Should Ubuntu detect the second hard drive and show it under "Places?"  If so, where can I find the second hard drive's contents?

2)  If the mysterious "lost & found" file is the second hard drive, how can I access it?

Thanks in advance.

Stephen

---

### Post by nixscripter on 2008-10-28
1. I don't know how it will show up on the desktop, but it should show up a list of devices. Try opening a terminal and running: ```
ls /dev/hd*
```

And you should get **hdb** things as well as **hda** things. hdb should be the new drive, and hda should be your main hard drive. This assumes you hooked up the second drive as primary slave; secondary master is **hdc**, secondary slave is **hdd**, and so on.

2. "Lost and Found" is an artifact of the ext3 filesystem. If data is found during a filesystem check it doesn't know what to do with, it goes under there. I don't think it's related to your disk.

---

