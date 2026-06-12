---
title: "USB flash disk: No Medium Found"
date: 2009-09-16
forum: Hardware
---

### Post by taquinas on 2009-09-16
I was sending multiple transfers to the removable flash disk when it stopped responding. I removed it re-inserted to find that it won't mount. It appears in Places/Computer but when clicked says Unable to mount location. It had a fat32 file system. 
1. Doesn't show up in gparted and fdisk says unable to open.
2. dmesg shows usb stick being attached.
3. fsck and e2fsck says: No medium found while trying to open /dev/sdd
4. fsck.vfat says: open /dev/sdd:No medium found
5. Same thing happens in xp, cannot format or access but shows that it is attached. Even the manufacturers disk recover software doesn't see usb stick. 
6. mount -t vfat /dev/sdd /media/flash/
    mount: No medium found


Any help would be appreciated. About to give up and throw it in the trash. 
More importantly how do I avoid this in the future when usb stick stops responding? Is there a force umount?

---

### Post by Dark_Stang on 2009-09-16
Have you hooked it up to another computer?
What does the Disk Management Utility in XP show? 0b free of 0b?
It may have just gone out on you. I've only had 2 flash drives die on me out of about 10. I've had one that one day decided it was going to be 1/2 the capacity it was the day before, and I've had several others that have gone through washing machines dozens of times and be just fine.

---

