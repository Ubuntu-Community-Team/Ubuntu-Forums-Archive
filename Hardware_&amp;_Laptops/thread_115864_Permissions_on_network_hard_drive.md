---
title: "Permissions on network hard drive"
date: 2006-01-11
forum: Hardware &amp; Laptops
---

### Post by darrenc on 2006-01-11
Hi, I have a question about permissions on an external hard drive.

The drive in question is a LinkStation network drive.  It is attached to my network hub and visible on all systems on my network.  I've just added the drive so I can put my music and personal documents in a common place that can hold them all and that's available network-wide without having to have other computers turned on.  My problem comes in when I mount it as a local drive in Ubuntu.

I can mount the drive at the command line or by fstab, however once it's mounted the file ownership is root only, and it won't allow me to change the ownership or grant write access to anyone other than root.  If I connect to the drive by samba, I have full user level permissions.  Even side by side file browser windows give me different permissions - if I create a folder or document as a user in the network browser it gives me full access, but at the same time it instantly shows the same folders and documents in the file browser but with only root level write access.

As for the music, If I don't mount the drive, the music files won't play as XMMS doesn't understand smb.  Once I mount it, they play fine but then I have no access to make changes to tags and such.  Of course moving documents there is useless if any changes I make can't be saved.

So, I guess my question is how can I mount the drive as myself, rather than as root?  I'm not new to linux, but I'm only a casual user so a lot of this kind of stuff is a mystery to me and I've never had to mount an external drive before.  Of course, I know that the mount command must be run as root.  I've specified in the options  column in fstab my username and password and included an rw, but it makes no difference in the ownership or in the write level access - it still doesn't give it to me.  The device itself is configured to allow anyone full access without a username or password required, it seems that it's only the process of mounting it in Ubuntu that chages this. 

Thanks for any suggestions anyone may have.

---

### Post by fourchannel on 2006-01-15
in the fstab file, you might try adding 'user' to the options string. also you might add 'fmask=777,dmask=777' to the options line also. not the best fix, but the only one I could think of.

---

### Post by darrenc on 2006-01-16
[QUOTE=fourchannel]in the fstab file, you might try adding 'user' to the options string. also you might add 'fmask=777,dmask=777' to the options line also. not the best fix, but the only one I could think of.[/QUOTE]

Thanks.  I added the fmask and dmask and that at least gets me write permissions.  That's good enough for what I need at the current time, so I'll just go with that for now.  Eventually, I'll have to figure out how to keep my file ownership, but that's down the road a ways.

Again, thanks.

---

