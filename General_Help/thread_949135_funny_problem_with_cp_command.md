---
title: "funny problem with cp command"
date: 2008-10-15
forum: General Help
---

### Post by elustran on 2008-10-15
I was trying to backup my /etc directory manually using:

```
sudo cp -rv /etc /media/backup-directory/etc
```

The verbose mode showed the files being copied over, but when I looked in my backup directory, I found an empty folder.  I tried a second time and the verbose output also showed something regarding files being removed.  I checked in my trash, and there was a shiny new 'etc' folder with all my stuff in it.  I deleted the locked 'etc' folder in my directory and copied it over from the trash in the gui, which worked just fine...

I'm not sure quite what happened
I made the backup directory from sudo, I think, and the first time I tried copying, I forgot the -r and used -p instead.

---

### Post by Cl0ud9 on 2008-10-15
Someone else may be able to provide more information, but I believe the cp command can have problems with hard links. For copying whole directories recursively its better to use:
```

$find /dir_to_copy -depth -print0 | cpio –null –sparse -pvd /backup_dir

```

This link may be of some use:
[http://www.us.debian.org/doc/manuals/reference/ch-tips.en.html#s-archiving]("http://www.us.debian.org/doc/manuals/reference/ch-tips.en.html#s-archiving")

---

