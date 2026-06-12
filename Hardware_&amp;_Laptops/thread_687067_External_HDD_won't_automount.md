---
title: "External HDD won't automount"
date: 2008-02-03
forum: Hardware &amp; Laptops
---

### Post by YodaMstr on 2008-02-03
I have a SeaGate FreeAgent 250G external HDD.

Problem is, it won't automount or show up in my media folder.  I made a directory in the mnt folder and I can access it that way, but I'd rather have it show up in media.  I've got:

```
# /dev/sdb2 /media/sdb2               ext3           defaults,umask=007,gid=46 0       1
```

in my fstab, but that isn't working.  So, any help?

---

### Post by Yellow Pasque on 2008-02-03
You do know that having the '#' sign in front of a line comments it out and it won't be read, right?
Some other things to check would be that the the directory /media/sdb2 exists (the command: *file /media/sdb2* should report that it's a file of type directory). Also, *cat /etc/group | grep 46* should return a line like:
> plugdev:x:46:haldaemon,<your user name here>

---

### Post by logos34 on 2008-02-03
you have it commented out.  Remove the '#'

---

### Post by YodaMstr on 2008-02-03
I tried it without that first, but still with no luck.  Also, all my other drives are commented out like that.

---

### Post by Yellow Pasque on 2008-02-03
Ok, try:
```
/dev/sdb2   /media/sdb2    ext3     rw,user,auto,exec,umask=007,gid=46    0       1
```

---

### Post by YodaMstr on 2008-02-03
That's getting closer.  I uncommented it and tried, and it'll show up under computer, but it won't let me access it.  It doesn't show up in media at all.  I tested and was able to get it to autodetect and mount when I had it plugged in from startup, but there's got to be a way to plug'n'play it, no?

---

### Post by Yellow Pasque on 2008-02-04
Hmm. Let's try:
```
/dev/sdb2   /media/sdb2    ext3     rw,user,auto,exec,uid=1000   0  1
```

---

### Post by logos34 on 2008-02-04
> **YodaMstr said:**
> I tested and was able to get it to autodetect and mount when I had it plugged in from startup, but there's got to be a way to plug'n'play it, no?

what about

system>prefs>removable drives and media>storage tab>check 'mount removable drives when hot-plugged'

does that help?

(the default mountpoint is '/media/disk', '/media/disk-1', etc.)

---

### Post by YodaMstr on 2008-02-04
Thanks for the help all.  I'll try working on this again in the morning, as right now I'm exhausted.  A note before I leave though:  logos, that option is checked by default on mine.  I checked again just to be sure for you, so that's not it. :p

Thanks all, see you around if you're on tomorrow when I'll inevitably need help.

---

### Post by YodaMstr on 2008-02-04
Temujin, that doesn't work either.  Again, if I uncomment it it will show the drive under computer whether plugged in or not, but when I try to access it when the drive is plugged in, it'll say that /media/sdb2 doesn't exist.  How would I go about finding the uuid of the drive?

---

### Post by Yellow Pasque on 2008-02-04
> How would I go about finding the uuid of the drive?
This will show you the UUID's of your filesystems:
```
cd /dev/disk/by-uuid; ls -l
```

I think this might be more of an issue with gnome-volume-manager or the hotplug script. I will do some more reading and get back to you if I think of anything.

---

