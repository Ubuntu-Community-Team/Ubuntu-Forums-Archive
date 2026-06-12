---
title: "Can't Mount External Comstar HD"
date: 2009-07-31
forum: Hardware
---

### Post by r557 on 2009-07-31
Before getting rid of windows vista, i backed up all my files on a comstar external hard-drive.

Whenever i go into Places > Computer it seems as though it can find the external drive, but whenever i click on it to open it always states "Unable to mount location".

How can i add the HD without formatting it and losing my data?

---

### Post by Shig on 2009-07-31
Hi

Is the drive NTFS? If so, you probably did not use "Safely remove this hardware" before unplugging it.
Linux will refuse to mount NTFS volumes if they were note safely removed from the system.

If you can plug the drive back into a windows system, and then safely remove it, it should automagically mount and show up on your desktop when you plug it back into the Linux system.

If not, you can run ntfsfix (in the ntfsprogs package, you can install this with the Synaptic package manager or apt-get) to reset the journal, which will let you mount it.

When you plug the drive into your linux system, run dmesg, which will show you the kernel log, and the last entries in the log should show you the name of the device as it appears to linux - e.g. /dev/sdX1 - when X will be a lowercase letter. Be careful to get the right one for the USB hard drive, as you will also have an entry for your main hard drive.

You can run:
```
ntfsfix /dev/sdX1
```to fix the filesystem

After this completes you should be able to mount the drive under linux.

---

