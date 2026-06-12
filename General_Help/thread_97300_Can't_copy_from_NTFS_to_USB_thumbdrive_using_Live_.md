---
title: "Can't copy from NTFS to USB thumbdrive using Live CD"
date: 2005-11-30
forum: General Help
---

### Post by Jon L. Jacobi on 2005-11-30
I was totally stoked about using the 64-x86 5.1 Live CD as a data recovery vehicle until this little oddity occurred. I used the disk management app to enable the NTFS partition, at which point I could browse and open files. However, I was unable to copy a file directly to a mounted USB FAT32 thumb drive. 

The copy option was available on both the NTFS partition and the thumbdrive, as was paste on the thumbdrive. I cut and pasted as well as dragged the file directly over and while there was no error message, the file did not appear on the thumbdrive.

On the other hand, I was able to open a text file from the NTFS partition and re-save it to the thumbdrive. Permissions on the NTFS are read-only, and on the thumbdrive are read and write which indicates to me that I should be able to do this.

Is this a bug, or am I missing something?

Cheers, Jon :confused:

---

### Post by aysiu on 2005-11-30
Even though Ubuntu's live CD can be used as a recovery CD, it's not designed to be a recovery CD. It's designed to be a preview of the installer CD.

If you want a good recovery CD, Knoppix is designed to be a recovery CD.

Okay. But you have Ubuntu, not Knoppix. So let's deal with that.

NTFS is, in fact, read-only, and FAT is, in fact, read-write.

When you save on the thumb drive, does the file actually appear (as opposed to the ones you try to drag and drop to the thumb drive)? When you drag and drop, is there an error message, or do you just not see a file there?

---

### Post by Jon L. Jacobi on 2005-11-30
NTFS to FAT32 thumbdrive

Drag & drop: no error message but file doesn't show up.
Cut & paste: no error message but file doesn't show up.
Open from NTFS & save to FAT32 thumbdrive: file shows up, i.e., appears in a directory listing.

Other than this, U51 could work quite well for basic save-your-data-before-reformatting.

I'll download the Knoppix.

Cheers, Jon

---

### Post by Jon L. Jacobi on 2005-12-01
Tried this on a second machine and with the 386 version and the exact same problem. So close...:( 

Cheers, Jon :rolleyes:

---

