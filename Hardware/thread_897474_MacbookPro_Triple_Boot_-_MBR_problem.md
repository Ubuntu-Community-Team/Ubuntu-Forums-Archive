---
title: "MacbookPro Triple Boot - MBR problem?"
date: 2008-08-22
forum: Hardware
---

### Post by ben22 on 2008-08-22
Hi,

it turns out that my windows install is not starting.

Here is what I did:

[LIST=1]
[*]install mac os leopard
[*]create partition with Bootcamp for win, do not install win through bootcamp
[*]insert win cd, press c during start, install windows to win-partition (created with bootcamp)
[*]install drivers for win from mac os cd
[*]boot macos, create a new partition for ubuntu
[*]insert ubuntu cd, press c during start up, install ubtuntu:
[*]during installation delete the partition created for ubuntu, format it to ext3, use 1 GB for swap, but make sure that the free space is the same as it was before. all partitions start at the beginning
[*]in the last step of installation, click advanced: install GRUB to the ubuntu partition
[*]boot to macos, install rEFIt
[*]when starting windows now. It shows the black windows screen, windows logo on top, progress for a moment. then crashes and restarts computer (starting windows before ubuntu was installed was possible)
[/LIST]
  
*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    226377767  Mac OS X HFS+
 3      226377768    304502768  Basic Data
 4      310788136    390721927  Basic Data
 5      304502769    306455894  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    226377767  af  Mac OS X HFS+
 3 *    226377768    304502768  83  Linux
 4      310788136    390721927  07  NTFS/HPFS

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 226377768:
 Boot Code: GRUB
 File System: ext3
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 83  Linux, active

Partition at LBA 310788136:
 Boot Code: Windows NTLDR
 File System: NTFS
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 07  NTFS/HPFS

Partition at LBA 304502769:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 5, type Linux Swap

One assumption is that the MBR cannot handle the 5 partitions...

I am glad for any hints!

ben

---

