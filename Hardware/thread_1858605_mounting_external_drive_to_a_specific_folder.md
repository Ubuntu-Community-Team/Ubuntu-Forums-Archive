---
title: "mounting external drive to a specific folder"
date: 2011-10-12
forum: Hardware
---

### Post by mistafeesh on 2011-10-12
Hi,

I have an external HDD that I sometimes plug in to my ubuntu box. I'd like it to mount in a specific place so it can be shared easily via samba and apache (had no luck with symlinks etc).

If I add a permanent mount point it upsets the startup process, but it's hardly ever plugged in on startup.

any ideas?


thanks,

Dan

---

### Post by mistafeesh on 2011-10-19
I've still not managed to crack this one. Basically I want to somehow automatically run the following command (or equivalent) when the disk is connected:

mount /dev/sdc2 /var/www/stuff

editing fstab won't help as the disk is virtually never plugged in when it starts up, which means the startup procedure is interrupted, which is a pain.

any ideas?

---

### Post by plasmafusion on 2011-10-19
add "nobootwait" to fstab?

---

### Post by mistafeesh on 2011-11-02
ahah I didn't know you could do that! That's what I need. Thanks - I'll go and re-edit fstab

---

