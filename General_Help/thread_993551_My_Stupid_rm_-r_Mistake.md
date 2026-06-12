---
title: "My Stupid rm -r Mistake"
date: 2008-11-25
forum: General Help
---

### Post by MaindotC on 2008-11-25
I have two hard drives attached, sda which is my filesystem, and I have sdb mounted in /media/disk-1.  I have all this stuff in my home directory that I really shouldn't - iso's, movies, music, documents, especially my school's network shares that are mounted in ~/smb4k - and I want to move them to the separate drive.

So I'm in my home directory and I think I meant to type:
```

amd64@amd64-desktop:~$sudo rm -r /media/disk-1/*

```

but I typed:

```

amd64@amd64-desktop:~$sudo rm -r /media/disk-1 *

```

So I'm watching the red light on my hard drive do its thing, and after a while I see my wallpaper disappear and the shell says:
```

 "Cannot remove file smb4k/myfiles/<omitted>/<omitted> Permission denied.

```
and I'm like "wtf are you accessing my network shares?!?!"  I quickly Ctrl + C and examine my directories - yep, not only almost all of my home directory, but my network shares are wiped out too.  DUMB!!!!

In class we practised disaster recovery and TestDisk did pretty well so it's buzzing away right now - I dunno how it could possibly recover the network shares but perhaps since they were mounted in ~/smb4k that counts as a local store.  If not, I think the admins for the campus shares may do tape backups.  *Frustrated*

---

