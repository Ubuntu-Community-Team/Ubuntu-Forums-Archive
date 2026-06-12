---
title: "Some Samba shares just won't mount"
date: 2008-08-19
forum: General Help
---

### Post by negge on 2008-08-19
Alright here we go.

I have an Ubuntu server with some files I want to backup to a Windows computer. All computers are connected to an AD domain controller and I need to be able to mount one of the shared folders in Ubuntu.

This line in /etc/fstab doesn't work: *//termonova-file/shared /media/Backup cifs auto,credentials=/etc/credentials 0 0* - I get a "mount.cifs error 20: Not a directory". No matter what I do I can't mount it. Sometimes when I change the path a little bit I get a segmentation fault and have to reboot the server. HOWEVER: Using *smbclient //termonova-file/shared -U sam* I can access the share.

However, this one works (it's another computer on the network with another folder): *//termonova-backup/Ohjelmat /media/Backup cifs auto,credentials=/etc/credentials 0 0*

How come this is? Only difference between the servers is that the termonova-backup server (which I CAN mount) is a Windows 2003 server while the other one is a W2K server. I've tried using both cifs and smbfs (although that shouldn't matter I suppose as Hardy only uses cifs). Are there any logs I should be checking for errors?

What I've tried so far:
- mount with different credentials (tried both DOMAIN/user and just user)
- use smbfs instead of cifs and vice versa
- used the IP address instead of the hostname

Any suggestions would be really grateful, I hate the idea of having to backup my files using FTP or something just because this whole Samba/Cifs thing is messed up.

---

