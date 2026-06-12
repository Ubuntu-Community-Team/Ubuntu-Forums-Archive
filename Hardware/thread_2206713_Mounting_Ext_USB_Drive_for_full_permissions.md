---
title: "Mounting Ext USB Drive for full permissions"
date: 2014-02-20
forum: Hardware
---

### Post by orsome1 on 2014-02-20
First off I must say I am totally new to Ubuntu

I have edited my fstab file to automount my external HDD - it is formatted NTFS
I use this with Plex and works
However I have now installed Samba so my Win7 and Mac can access this drive on my Ubuntu machine
Both Windows machine and Mac can see the Samba shares and read them, however they cannot write to this drive. The Samba shares and permissions are correct as in Config file NTFS drive share - writeable is set to yes.

When try write to the drive from windows it advises - Do not have permissions.

I am thinking - could this be due to the mounting permissions in the fstab file?What should I be adding to the share lines to enable both the Windows machine and the Mac to be able to write to the Ubuntu machine? have fiddled with the one mounting but still not working.

UUID=F078DE5878DE1CE2 /media/ntfsdrive1 ntfs-3g defaults,auto,uid=1000,gid=1000,umask=000,fmask=133 0 0
UUID=8274FE9A74FE9061 /media/ntfsdrive2 ntfs-3g permissions,auto 0 1
UUID=7EE26DF2E26DAED9 /media/ntfsdrive ntfs-3g permissions,auto 0 1

---

