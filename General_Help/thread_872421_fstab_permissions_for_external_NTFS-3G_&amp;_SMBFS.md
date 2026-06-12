---
title: "fstab permissions for external NTFS-3G &amp; SMBFS"
date: 2008-07-28
forum: General Help
---

### Post by freakalad on 2008-07-28
This is a repost from a thread I got no reply to, so here goes...

Have 750 GB Maxtor external, NTFS.
Have a 750 GB Lacie NAS.

ntfs-3f, cifs, smbfs, samba & the rest installed.

I have 2 shares ready, with chmod 744 & chown me:users (id's 1000:100).

Been able to execute the following:
mount -t ntfs-3g /dev/disk/by-uuid/007C964A77FD9E3E /media/kool/
Mounts OK, but sets the permissions to: 777 root:root

Able to execute the following:
sudo mount -t smbfs //10.0.0.10/media /media/lacie_media
Mounts & sets permissions the same, but I'm unable to write to the share (but that may be due to a network rights issue).

I need help tweaking my /etc/fstab enties.

Want my original permissions of 744 me:users on my mounts.

Got this far:

UUID=00112233XXYYZZ /media/kool ntfs-3g defaults=rw,exec,user,auto,user_id=1000,group_id=1 00,dir_mode=0744,file_mode=0750 0 0
//10.0.0.10/media /media/lacie_media smbfs defaults=rw,exec,user,auto,user_id=1000,group_id=1 00,dir_mode=0744,file_mode=0750 0 0

Any user/process must be able to automatically mount any drive, but a hard mount must me skipped @ boot, to prevent undue long boot if drive/resource is not present.

Losing the plot with some of the new arguments.
Also, what are the significant difference in arguments when applying different protocols? Have nfs, hpfs & vfat/fat32 shares I want to mount too.
Considering 777 on these drives, and I KNOW that's SOOOO wrong...

Can somebody refer me to a concise resource?

Otherwise, is there some shell tool (pseudo-'gui'), like mc, that can make this hole process easier, with the correct options?

Please help

---

