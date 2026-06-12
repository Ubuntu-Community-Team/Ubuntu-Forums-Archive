---
title: "dual boot linux and xp- xp does not see unpartitioned space"
date: 2009-04-05
forum: Installation &amp; Upgrades
---

### Post by brookiew on 2009-04-05
I have the latest ubuntu installed on my computer, and wanted to add xp for a dual boot configuration.  I followed the instructions provided by 
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=4](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=4)

I made space for xp, by doing what they recommended which was using the ubuntu live cd "try ubuntu without any change to computer" and changed partition space and hit apply.  

When I put the xp disc in and run setup, it only recognizes the partitioned space, not the unpartitioned space.  It seems I have followed the directions exactly and am not sure what to try next.  Any help would be appreciated.

---

### Post by Didius Falco on 2009-04-05
Personally, I'd reboot with the Ubuntu Live CD and make a Primary partition in that free space. Then I'd format it to NTFS and retry the XP install.

I haven't done this myself, but it seems  like the next logical step to me.

---

### Post by ronparent on 2009-04-05
Where is that unpartitioned space, could it be an extended partition?  If not, how many primary partitions are already on the drive? XP will not install on an extended partitions or if there are already too many primary partitions (two I think).

---

### Post by x22 on 2009-04-05
for painless multiple-boot rule #1: install windows first

---

