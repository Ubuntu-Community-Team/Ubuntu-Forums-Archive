---
title: "shell command to mount usb drive just like gnome-volume-manager or hald does"
date: 2008-05-10
forum: Hardware
---

### Post by arch0njw on 2008-05-10
I have looked, I really have.  I have a feeling I am missing something subtle but completely obvious.

I want to, from the command-line, do exactly what the auto-mounting tools do when I turn on my external HDD.  I want to get a particular machine completely away from needing the head, and this is the one last things that is bugging me.

When I mount my WD Combo, this is what I see under /media:
drwx------ 6 my_uid root     32768 1969-12-31 19:00 WD Combo/

Every directory on that drive ends up with those same permits too.

1. I know I need to create the /media/mount_point -- no trouble there
2. I can set the permits on the mount point to be what I want
3. The mystery has been how to get the drive to mount with those permits for my_uid.  I just cannot seem to make that leap yet.  I have tried a number of different entries in my fstab an it just doesn't want to cooperate.

Here is how the drive appears in my mtab:
/dev/sdg1 /media/WD\040Combo vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree 0 0

Many thanks in advance for help on this.

---

### Post by arch0njw on 2011-06-19
Can you believe I'm still looking (perhaps just waiting) for an answer to this?  My hey hangup is getting the exact permissions.

---

