---
title: "ushare: multiple folders from command line"
date: 2008-11-11
forum: General Help
---

### Post by Meson on 2008-11-11
Ushare seems to be a rather finicky program.  Does anyone know if multiple content directories are supported from the command line?  For example:
```

$ ushare -n STUFF -i eth1 -f /dev/null -c ~/Music -c ~/Videos -v -x -w -t

```

this seems to list the Music fine, but the Videos directory is all messed it, it shows the music over again and none of the videos.

---

### Post by c$$lguy on 2008-11-19
I've seen the sample on uShare support page:
ushare -c /shares1 --content=/shares2
So in your case it would be
ushare -c ~/Music --content=~/Videos
I use /etc/ushare.conf to specify directories

---

### Post by c$$lguy on 2008-11-30
I used ushare configuration file to enter the directories. It works with no problem. In ushare.conf change directories line:
> # Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
it is separated by comma.

---

