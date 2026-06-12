---
title: "External Hard Drives are difficult if you are stupid."
date: 2008-11-11
forum: Hardware
---

### Post by caplancr on 2008-11-11
I am stupid.  I am trying to connect my external hard drive to my computer that's running ubuntu.  I go to places>simpledrive (the external hard drive) and it says "cannot mount volume".  From what I've read this should work, but it doesn't.  It also says that NTFS is in use?  How can I get my files off this hard drive?

---

### Post by taurus on 2008-11-11
Open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Coreigh on 2008-11-11
Did you remove this disk from a Window computer and put it in an external disk enclosure? If yes, and if Windows did not shut down cleanly you will get the files in use error (or similar) when you try to mount the drive. I do npt know if the is a way to force it, and it is probably not a good idea to try. But if you re-install the disk in the computer it came from, start it up, and shut it down properly the error should resolve. You may need to run a CHKDSK at Windows boot up to correct errors.

But as I said this is only if you removed this disk from a Windows computer that was not shut down cleanly.

---

