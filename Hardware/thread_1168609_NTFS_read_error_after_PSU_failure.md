---
title: "NTFS read error after PSU failure"
date: 2009-05-24
forum: Hardware
---

### Post by pete-wilko on 2009-05-24
Hi everyone,

i've got a problem where my pc had a PSU failure - the primary hard disk is fine, however the secondary disk is having read errors on any large files or files embeded deep in a dir hierarchy. I booted into XP to run chkdsk, chkdsk /f seemed to run ok but chkdsk /r is now hanging.

Problem is that either connected to mobo, or via USB enclosure, the HDD is being reported as different sizes. The disk itself is a 250GB barracuda. However in the BIOS its listed as 137GB and  acronis disk director in XP its listed as 128GB. In XP itself, explorer though lists it at the correct size of 230GB - and in acronis itself it says 128GB but then says it contains a 230GB ntfs partition.

Kinda confused, something needs to be reset - not sure how - but the HDD can be 'read' except for large files (eg >3MB) which if try to open produce read errors. Any help much much appreciated.  The read errors occur in both ubuntu and XP.  

The HDD in an external enclosure mounts fine in ubuntu and can navigate the hierarchy, but again its the read errors for large files, which seems to be platform agnostic.

Not strictly a problem with ubuntu at all, but some smart people here so any help would be awesome.

Cheers,
Pete

---

### Post by ddrichardson on 2009-05-24
If you can mount it, have you run testdisk on it?

---

### Post by pete-wilko on 2009-05-24
Hi,

thanks for the reply - I started to run it, but the size its detecting is 137GB - same as bios - the warning message is not to proceed unless the correct size is detected.  

Suggestions are for BIOS/jumpers/firmware.  Jumpers I think are ok.  I cant remember every installing any firmware for this HDD, but could look at that.  BIOS not sure about - again can't recall updating the BIOS firmware but it might have gotten hosed in the power failure, so can check what revision its at.

Thanks for the advice, 
Cheers,
Pete

---

