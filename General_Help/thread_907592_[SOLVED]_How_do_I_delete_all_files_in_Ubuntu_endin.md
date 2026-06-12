---
title: "[SOLVED] How do I delete all files in Ubuntu ending with the ~ character?"
date: 2008-09-01
forum: General Help
---

### Post by Rytron on 2008-09-01
Hi,
How do I delete all files in Ubuntu ending with the ~ character? As far as I know, these files were created by text editors making backups when saving.
I easily deleted theses ~ files in Kubuntu by doing a search with the criteria *~
However when I do this in Ubuntu it says there are none, even though in the interpreter I can see them.
Please help.
Thank you.

---

### Post by joenix on 2008-09-01
Files ending in ~ are treated as hidden files by the Nautilus file manager.
If you enable "Show Hidden Files" in the View menu, you should be able to find them.

---

### Post by drs305 on 2008-09-01
This command will find all files ending with ~ in your /home folder/subfolders:
```
find ~ -type f -iname *~
```

Remember that the ~ ending may mean a file is currently in use.
You can add the switch " -atime +XX" with XX being integers to find files accessed more than XX days ago.

---

### Post by Rytron on 2008-09-01
Thanks guys for your prompt replies.

:KS

---

### Post by Vivaldi Gloria on 2008-09-01
Hi Rytron.

Building on drs305's advice, the command

```
find /path/folder -name "*~" -exec rm -fv {} \;
```

will delete all of them in /path/folder. First test with

```
find /path/folder -name "*~" -exec echo {} \;
```

If you use ~ for /path/folder then it'll look into your home folder.

Cheers.

---

