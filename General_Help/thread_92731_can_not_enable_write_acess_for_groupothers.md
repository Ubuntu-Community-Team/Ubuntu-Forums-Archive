---
title: "can not enable write acess for group/others"
date: 2005-11-20
forum: General Help
---

### Post by dragonflyFZX on 2005-11-20
hi,

can someone explain me why i can not enable write access for group or other users (and then explain me how i can:)  )?  I want members belonging to my group to be able to write to an external hard drive.  The drive is mounted on
/media/maxtor
which is owned by me (a mortal user)and my group. I thought a simple:

chmod -R g+w /media/maxtor

would do, but no.  I can change read and execution access tho.

---

### Post by Bachstelze on 2005-11-20
Check your /etc/fstab file. Maybe your drive is mounted read-only.

---

### Post by dragonflyFZX on 2005-11-20
yes it is, but i thought i could override that with chmod, and especially with sudo chmod, anyway, i will just change the fstab then.  Thanks.

---

### Post by dragonflyFZX on 2005-11-21
ehh i correct my previous message, there seems to be something else going on here as:

/dev/sda1       /media/maxtor   auto    rw,user,noauto  0       0


i did mount my drive in read write mode

---

### Post by hw-tph on 2005-11-21
Either pass the gid option to mount (followed by the actual gid - see /etc/group for the exact number) or specify it in /etc/fstab so it will always mount as that group.

```
mount /dev/scd1 /mnt/mountpoint -o uid=1000,gid=1014
```...or whatever.

Håkan

---

### Post by dragonflyFZX on 2005-12-01
ok, this all helps, but this seems to overrule the permissions  i have set on specific folders on the drive itself.  For example, some files should only be accesible by the owner, other by the group. Each time I reboot, the permissions are all back to the ones passed by fstab.  Is this normal?  How can i change this (ie. that the permissions stay as i changed them in the previous session)? it is a removable drive, so...  And another thing.  How can i make  sure the drive always gets mounted in the same location.  That is, if i unplug the drive that was  for instance /media/sda1, plug another drive in, and then plug the first drive in again, i want it to be sda1 again (or something else, but just something static).  Now it gets mountes somewhere like /media/sdc1.

---

### Post by cgjones on 2005-12-01
I think that if you change user to users in your fstab, it might help. Check out the man pages for fstab and mount.

---

### Post by aysiu on 2005-12-01
Can't you put the other users in your user group?

---

### Post by dragonflyFZX on 2005-12-01
[QUOTE=cgjones]I think that if you change user to users in your fstab, it might help. Check out the man pages for fstab and mount.[/QUOTE]
just did that, did a reboot, but same deal...

---

