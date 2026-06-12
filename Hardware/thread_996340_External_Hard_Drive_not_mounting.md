---
title: "External Hard Drive not mounting"
date: 2008-11-28
forum: Hardware
---

### Post by SAHChandler on 2008-11-28
Hey There,

I'm trying to mount an external hard drive that was a windows XP install.
However when I mount it this is the error I get.


Record 147404 has no FILE magic: Invalid argument
ntfs_file_record_read failed #2: Input/output error Failed to map extent inode: Input/output error Failed to open index allocation attribute. Directory inode 0x5 is corrupt or driver bug: Input/output error Failed to mount '/dev/sda1': Input/output error NTFS is either inconsistent, or you have hardware faults, or you have a SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on windows then reboot windows TWICE. The usage of the /f parameter is very important! if you have SoftRAID/FakeRAID then first you must activate it and mount a different device under the /dev/maper/ directory, (e.g./dev/mapper/nvidia_eahaabcc1).
Please see the 'dmraid' codumentation for details


is there a way to fix this without having to do the first option? or is this drive borked?

Any and all help is greatly appreciated.

---

### Post by Coreigh on 2008-11-28
How was this disk used before? Was it always an external hard drive? or is it a plain hard drive in a USB encloure? Is there anything on the disk you want to keep? The errors seem to indicate it was used in a RAID volume, or at the veryleast uncleanly unmounted from its previous use.

If this is just a spared disk and there is nothing you need to save from it, then just reformat it using gparted (System >> Administration > Partition editor)

If there is stuff to be saved I would try to back track. Reinstall the disk to its old configuration and recover the data. Back it up to CD. And then wipe the disk and start over.

---

