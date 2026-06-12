---
title: "cannot change folder permissions"
date: 2005-11-23
forum: General Help
---

### Post by Doobiedo on 2005-11-23
Hi there.

im trying to set up samba to act as a file server for sharing mp3s between a group of win xp boxes.

ive created a fat32 partition mounted on /shared which can be accessed from the xp machines, however the xp boxes cant write to the folder.

ive set the permissions in /etc/samba/smb.conf 

create mask = 0777
directory mask = 0777 

when i try to chmod the /shared or /shared/music folders nothing happens, no errors, no change of permissions, nothing.

can anybody help me?
thanks

---

### Post by fourchannel on 2005-11-23
first off, since it's a network share, you don't have to format the drive for FAT when it's not actually on a windows machine.

format your music partition to EXT3.

the reason nothing ever changes is that the FAT32 file system does not support permissions and other identifying stuff like that.

samba will automatically work it out so that the XP machines can recieve the file, regardless of the actuall filesystem it shares out of.

---

