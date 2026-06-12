---
title: "Cannot change permissions on a hfsplus filesystem"
date: 2010-01-29
forum: Hardware
---

### Post by thetrout on 2010-01-29
Hi,

I am doing data recovery from a failed iBook G3. The file system on the HDD is HFSPlus. I can mount the drive in Ubuntu 9.10 no problems and I can browse the drive.

However, because of the permissions I cannot access the folder with the data I need. Everytime I try and alter the permissions or take ownership of something I get the following message:

ubuntu@ubuntu:/media/Kate,s HD/Users/user$ chown root Documents
chown: changing ownership of `Documents': Read-only file system

and the permissions do not take effect. I note that if you issue a straight "sudo mount" command, that the drive is showing as mounted for rw. 

/dev/sdb5 on /media/Kate,s HD type hfsplus (rw,nosuid,nodev,uhelper=devkit)

I have also installed hfsprogs, hfsutils and hfsplus but I still cannot write to the file system in order to edit the permissions.

Is there a way around this, any advice would be much appreciated :) I can provide further info if needed :)

Regards,

thetrout :)

---

### Post by tubasoldier on 2010-01-29
you can read a journaled hfsplus filesystem but can not write to it.
thus you can not change permissions

---

### Post by thetrout on 2010-01-29
Ok, Thanks for that... I was beginning to think this and after further research I discovered that journaling is enabled by default... :(

Is there any way I can disable journaling in Ubuntu as I do not have another Mac to hand :(

Regards :)

thetrout

---

### Post by tubasoldier on 2010-01-30
i'm not sure if you are still watching this thread. but in order to actually change permissions you will need a mac.

on the on the other hand, you can still get the files in Linux. 
alt+f2
sudo nautilus

then you should be able to at least view the files and copy them. 
Note that after you make a copy of them you will need to change the permissions as they will all be owned by root.

---

### Post by thetrout on 2010-01-30
Many thanks for that :) I'll give that a go and post back the results ;)

---

