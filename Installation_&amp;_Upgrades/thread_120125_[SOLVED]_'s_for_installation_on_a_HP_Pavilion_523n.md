---
title: "[SOLVED] ?'s for installation on a HP Pavilion 523n with internal recovery partition."
date: 2006-01-20
forum: Installation &amp; Upgrades
---

### Post by RavenOfOdin on 2006-01-20
Hi. Can anyone help me here, and give opinions on this situation to someone who is using a shared computer and can't risk a complete meltdown? I've read everything possible on the situation and I don't consider myself to be an idiot by any stretch . . . 

I just want to have all my bases covered, and covered again. So here goes:

I ordered the Ubuntu 5.10 CD from ShipIt in October of last year. The only computer I am able to put it on at the moment is a Pavilion 523n with Windows XP Home pre-installed. I got it in 10/2002 and it doesn't have a recovery CD creator as later models do.

But what it DOES have, is a 70GB NTFS partition and a 10GB FAT32 boot partition for the purpose of system recovery. This is all the space on the drive and nothing is left to install Ubuntu.

So I have to resize partitions through utilities. PartitionMagic didn't do it for me (Error 1513 plus horrible Symantec support) and neither did Acronis Disk Director. 

Partman, on the Ubuntu disc, didn't really ship with the clearest documentation as to whether or not the partition work (resizing) is non-destructive (?) All it said was that it supports NTFS partitions, nothing about specific versions (3.1 minimum as specified on Microsoft's site) or in what circumstances this will kill my C: drive - Since I've heard about NTFS rolling over and playing dead after resize attempts. 

The only thing left for me was to check into HP System Recovery. This apparently can be done from the hard drive and all reason says this partition will be left intact should the data be corrupted, thereby enabling a format . . .clean partitioning. . .and re-install of Windows XP with factory settings on. I just need to "press F10 repeatedly at the blue screen with the HP logo." Yay. :)

Does anyone here have a HP comp with System Recovery, or know if this will be enough in the worst case?

---

