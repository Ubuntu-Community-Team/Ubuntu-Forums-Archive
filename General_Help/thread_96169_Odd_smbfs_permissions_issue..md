---
title: "Odd smbfs permissions issue."
date: 2005-11-28
forum: General Help
---

### Post by IanLowe on 2005-11-28
I'm a couple of weeks into using Ubuntu, and loving it - I'm dual booting into XP still, but for fewer and fewer things.

one of the biggies - accessing my home directory on our SBS 2003 Server. I'm mounting the share using mount -t smbfs, and all is well...

except for one gotchca!

If I open up the mount point in Nautilus, I can see the two folders inside my home share, called "My Documents" and "Windows Profile".

Although the permissions on the windows side are *identical*  (they both inherit all permissions from the parent folder), one appears as belonging to root with 555 permissions, and the other as 777.

Inside the Windows Profile folder (that's the one with 777), roughly half of the folders show as 555, the others as 777 - the folders always have the same settings, but there doesn't seem to be a pattern to it.

Any ideas?

---

### Post by IanLowe on 2005-11-30
(bump)

any ideas?

I'm finding this really strange, as all of the other SMB shares I have mounted in my /etc/fstab (on the same server even!) are perfect.

quite odd. :confused:

---

### Post by jliedeka on 2005-11-30
in your /etc/fstab, you should be able to add uid/gid options to make you the owner of the mount points.

example:

//mywinserver/myshare  /mnt/samba/mywinshare  username=remoteuser%remotepw,uid=localuser,gid=localgroup  0  0

(ignore the space in localgroup, I didn't put it there)

---

### Post by IanLowe on 2005-12-02
Yay!

That helped nicely - whilst the folders still mounted with permissions 555, they now belonged to me, so I could chmod them back to useful values.

Thanks! :)

---

