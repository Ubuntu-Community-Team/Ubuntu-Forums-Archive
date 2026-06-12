---
title: "Storage: Input/Output error on a 1.5 TB ext hard drive. Need help."
date: 2009-10-16
forum: Hardware
---

### Post by Xomm on 2009-10-16
Hi,

I've bought a 1.5 TB external drive a couple months ago and it works without a hitch.

Then while using Ubuntu, while copying files back and forth, I kept getting "Error copying files: input/output error"

Rarely, some files do go though, but I've done several copy tests to various devices and concluded it's a problem with the hard drive, not my Ubuntu installation.

I booted into my Windows XP partition and tried to access the drive with no success. On booting, a message box would appear saying something along the lines of "Drive K:\ is corrupt and unreadable, please run ChkDsk utility"

When accessed in windows explorer, the only file in the hard drive is ".goutputstream-LUOO1U", 48 KB, but when opening Properties, the hard drive still has the 320 GB originally on it.


Could anyone explain to me what this input/output problem is? and provide a solution if possible?

EDIT:

When the file seen in XP is opened with notepad, I get random gibberish, seemingly with bits of my old Word Documents in it. 

This is really bizzare.

---

### Post by Giblet5 on 2009-10-16
The filesystem is corrupted/damaged.

This can be due to a power-fail during write (or defrag).

Since you said that you tried to access it from Windows, I'll assume that it is NTFS or FAT32.

From Windows, you can check/fix it with ```
chkdsk/f X:
``` where X: is the assigned drive letter. Or, you can right-click the drive letter in Explorer, select Properties, Click the Tools tab, and click the Check button (with repair enabled).

From Ubuntu, for NTFS: ```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdXN
``` where X is the 1.5T drive and N is the NTFS partition in question.

From Ubuntu, for FAT32: ```
sudo fsck.vfat /dev/sdXN
``` where X and N are as described above.

---

### Post by Xomm on 2009-11-02
Checkdsk failed.

I backed up data through Ubuntu and reformatted as NTFS w/ windows, and i/o error is gone.

Would that mean the problem is fixed?

---

