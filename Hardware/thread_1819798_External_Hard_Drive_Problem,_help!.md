---
title: "External Hard Drive Problem, help!"
date: 2011-08-06
forum: Hardware
---

### Post by Chocopuffs on 2011-08-06
Please help! Up until last night my USB external hard drive was working perfectly fine. However, now whenever I plug it in it gives me these errors: 

Error mounting: mount exited with exit code 13: The disk contains an unclean file system (0, 0). The file system wasn't safely closed on Windows. Fixing. ntfs_attr_pread_i: ntfs_pread failed: Input/output error Failed to read NTFS $Bitmap: Input/output error NTFS is either inconsistent, or there is a hardware fault, or it's a SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows then reboot into Windows twice. The usage of the /f parameter is very important! If the device is a SoftRAID/FakeRAID then first activate it and mount a different device under the /dev/mapper/ directory, (e.g. /dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation for more details. Failed to sync device /dev/sdb1: Input/output error Failed to close volume /dev/sdb1: Input/output error 

and:
DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

i'm working with ubuntu 10.10 single boot (vista corrupted on my computer so i had to replace it, and funds are rather short). there are hundreds of thousands of files on that hard drive (My Passport WD) that i really need to get back. and ideally i'd like for my external hard drive to be functional again. i'm not very proficient in computer lingo and knowledge, but i would appreciate any and all help. google has failed me and i don't know what to do 8/

---

### Post by jerrrys on 2011-08-06
you did not properly dismount in windows, but you don't have windows.

maybe the fix would be to plug it into a windows machine and do a dismount.

---

### Post by Chocopuffs on 2011-08-06
my desktop runs on vista (sadly) so perhaps that's where the problem originated. when i plug my hard drive in to that, it just freezes up the computer... what do you suggest?

---

### Post by jerrrys on 2011-08-06
sounds to me you need to execute the instructions in your first post in windows and sorry, but i do not know how to do that.

---

