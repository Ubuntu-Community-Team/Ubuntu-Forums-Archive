---
title: "[SOLVED] Easy question about /tmp"
date: 2008-09-16
forum: General Help
---

### Post by N4zgu1 on 2008-09-16
I just want to ask how /tmp should look like, which files does it contains.

Im asking this because I made some crazy stuff and now I want to return the /tmp folder to its previous state

Anybody who has not modified /tmp can answer me this question

---

### Post by mb_webguy on 2008-09-16
The /tmp folder is for temporary files, like the temp folders in Windows.  These files are usually not kept from one reboot to the next, so you should be able to delete anything in the /tmp folder without any harmful side effects.

---

### Post by Krupski on 2008-09-16
> **N4zgu1 said:**
> I just want to ask how /tmp should look like, which files does it contains.

Im asking this because I made some crazy stuff and now I want to return the /tmp folder to its previous state

Anybody who has not modified /tmp can answer me this question

Not a whole lot in mine. I've never touched it, so it's "virgin".

```

root@storage:/# ls -laF /tmp
total 4
drwxrwxrwt  3 root root   60 2008-09-16 17:02 ./
drwxr-xr-x 21 root root 4096 2008-09-15 18:26 ../
drwxr-xr-x  2 root root   60 2008-09-16 00:40 .winbindd/
root@storage:/# ls -laF /tmp/.winbindd/
total 0
drwxr-xr-x 2 root root 60 2008-09-16 00:40 ./
drwxrwxrwt 3 root root 60 2008-09-16 17:02 ../
srwxrwxrwx 1 root root  0 2008-09-16 00:40 pipe=

```


-- Roger

---

### Post by -Zeus- on 2008-09-16
just blow it away - sudo rm -rf /tmp/*

just make sure you're not downloading anything at the time; if you want to be extra safe, just close all your applications first and/or log out

---

### Post by niteshifter on 2008-09-16
Hi,

> just blow it away - sudo rm -rf /tmp/*

... and quite a few things will probably quit working right. Important things like keyrings and virtual file systems and ssh and such. Depends - a lot - upon what software is installed.

Unless you've "customized" the INIT process(es) and/or modified permissions for /tmp a reboot will delete all of /tmp and repopulate it.

---

### Post by N4zgu1 on 2008-09-16
thanks all of you were right after the reboot everything was the same

---

### Post by Krupski on 2008-09-17
> **N4zgu1 said:**
> thanks all of you were right after the reboot everything was the same

Since you need /tmp although it's rarely used, you could set your system to load it into ram. It would be fast and it goes away and gets recreated fresh and empty at each reboot.

To do it, simply add this line to your '/etc/fstab' file:

```

tmpfs    /tmp    tmpfs    defaults,noatime,mode=1777    0    0

```

This means "mount the /tmp directory in the 'tmpfs' file system (ram), use the tmpfs filesystem, use default permissions, don't bother updating file access times and create with mode 'drwxrwxrwt', don't dump it and don't fsck (filesystem check) it".

Good luck.

-- Roger

---

### Post by Krupski on 2008-09-17
> **-Zeus- said:**
> just blow it away - sudo rm -rf /tmp/*

just make sure you're not downloading anything at the time; if you want to be extra safe, just close all your applications first and/or log out

Your command line is fine... but a general warning to EVERYONE to be VERRRRRYYY careful with any kind of "sudo rm -rf" command. One slip of the keyboard could nuke most to all of your Linux installation.

Be careful!

-- Roger

---

### Post by Trebaruna on 2008-09-17
> **Krupski said:**
> Since you need /tmp although it's rarely used, you could set your system to load it into ram.
This has the added benefit of not leaking information if you've encrypted parts of your filesystem.

---

