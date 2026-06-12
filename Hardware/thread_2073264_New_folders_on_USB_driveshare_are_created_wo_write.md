---
title: "New folders on USB drive/share are created w/o write permissions"
date: 2012-10-19
forum: Hardware
---

### Post by virdung on 2012-10-19
I have a annoying problem, and being a ubuntu newbie I think I've reached the end of what I able to figure out myself.

Just moved from a win xp to kubuntu 12.04 and using the pc as a samba file server.
Everything seems fine except the fact that all new folders created without write permissions. Samba permissions were set with dolphin and permitted all users full control.

I've already runeed chown and chmod on the entire drive, and when I run mount i get this output for the drive i question:
> 
/dev/sdd1 on /media/ICYBOX type ext4 (rw,nosuid,nodev,uhelper=udisks)
running ls -la gives me this, where New folder has been created after I've chmod'ed the  share root.
> 
drwxrwxrwx 182 vir vir 20480 Oct 16 20:16 Docs
drwxr-xr-x   2 vir vir  4096 Oct 18 22:57 New folder
Anything else I need to check?

Thank you

---

### Post by virdung on 2012-10-19
Hmm, might have solved it.

dismounted the external drive and re-mounted it seems to have done the trick...

---

