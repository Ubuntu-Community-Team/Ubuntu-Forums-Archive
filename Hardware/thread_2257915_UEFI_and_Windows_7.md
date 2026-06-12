---
title: "UEFI and Windows 7"
date: 2014-12-23
forum: Hardware
---

### Post by azurehi on 2014-12-23
Do new windows 7 computers desktops or laptops come with UEFI?  Another way of asking this question is are motherboards made after a certain date come with UEFI rather than standard BIOS?  I see many ads for windows 7 computers at good prices and am interested in dual booting with ubuntu (or other linux distro) Without the hassle and uncertainty of dealing with UEFI.  Thanks.

---

### Post by weatherman2 on 2014-12-23
Pretty much all new PCs will come for UEFI so that they can be Windows 8 compliant.  Most of them allow you to disable secure boot and/or boot in "legacy" mode, however, so as long as you can do that, no need to worry about UEFI.

---

### Post by oldfred on 2014-12-23
Yes & no.

Many Windows 7 systems with Intel i-series chips were early UEFI, but Windows 7 was installed in BIOS boot mode on MBR drive. A few Windows 7 systems just before Windows 8 came out were installed in UEFI boot mode. 
With any new Windows 7 system now, it may be either, but hardware is probably UEFI and you may still have some of the UEFI issues of settings. You have to set UEFI/BIOS to boot in the mode you want, and may have more settings whether in UEFI or CSM/BIOS to set to have system work correctly. Old BIOS often needed no settings or just a couple.
Note that all Macs since they changed to Intel processors are UEFI.

Actually UEFI is slightly better, its just with Windows secure boot and how vendors are internally modifying UEFI to only boot the Windows entry that are causing all the dual boot headaches. And being new we have to learn new ways to do things.

 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by azurehi on 2014-12-23
Thanks for the information and suggestions.

---

