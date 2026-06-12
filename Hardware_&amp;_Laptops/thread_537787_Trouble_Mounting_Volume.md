---
title: "Trouble Mounting Volume"
date: 2007-08-29
forum: Hardware &amp; Laptops
---

### Post by jbellonejr on 2007-08-29
Okay, guys, I have a problem here. 

I have an old system here at work that was running MS-DOS (not exactly sure what version, but the system still works). It was running with 2MB of memory and on a 40MHZ processor. We *need* to pull this software off the drive, but the problem is that Windows doesn't recognize the drive and a neither does Linux.

When I try to mount the volume using both vfat and msdos it doesn't recognize the volume information. I am getting "bad superblock on /mnt/hda, wrong fs type or other error"

When I check the dmesg I only get information as such:
FAT: invalid media value (0x01)
VFS: Can't find a valid FAT filesystem on dev hda.
FAT: invalid media value (0x01)
VFS: Can't find a valid FAT filesystem on dev hda.
FAT: invalid media value (0x01)
VFS: Can't find a valid FAT filesystem on dev hda.

Any suggestions? The hard-drive does work on the system it was in, and if you attempt to boot from it goes into DOS but sits on the prompt. 

I want to attempt to use DOSBox for the software, or at the very least have a copy of it in case the system finally does go down for sure.

Any help would be appreciated. Thanks guys.

---

