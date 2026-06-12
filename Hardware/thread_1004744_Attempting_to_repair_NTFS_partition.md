---
title: "Attempting to repair NTFS partition"
date: 2008-12-07
forum: Hardware
---

### Post by jamesbeatty on 2008-12-07
I have three hard drives in my computer -- Ubuntu has a partition on one, and the remainder, along with the other two, is NTFS (dual-booting Vista). Lately, Ubuntu has been unable to mount one of the hard drives -- not the one it's on. It gives the error about NTFS still being mounted, even though Vista seems to shut down normally.

At any rate, I ran ntfsfix to see if I couldn't fix the drive. Here's the output:

```
james@spartacus:~$ sudo ntfsfix /dev/sda1
[sudo] password for james: 
Mounting volume... FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... FAILED
Correcting differences in $MFTMirr record 3...OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
```

It's been sitting like that for about 30 minutes. I'm thinking I might be better off running chkdsk in Vista, but I don't know if shutting off Ubuntu while ntfsfix is working could damage the disk.

---

### Post by eotakos on 2008-12-16
you are asking a question here, but i didn't know about ntfsfix , so thank you! - i'm facing an ntfs error myself and i can't fix it with neither gparted, or testdisk so a ntfs fix might be what's needed :-)

---

### Post by eotakos on 2008-12-17
there is something else i'd like to add at this thread, you never force-stop an application manipulating file systems especially the ones manipulating partition tables, because it is most likely that you'll break something.

---

### Post by vanadium on 2008-12-17
You should only use MS Windows to repair ntfs volumes.

---

