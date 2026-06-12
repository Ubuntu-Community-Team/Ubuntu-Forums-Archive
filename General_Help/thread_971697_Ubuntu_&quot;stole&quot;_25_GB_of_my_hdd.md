---
title: "Ubuntu &quot;stole&quot; 25 GB of my hdd"
date: 2008-11-05
forum: General Help
---

### Post by adieb on 2008-11-05
Hello

I have an annoying problem:
```
df -h /home
Dateisystem            Size Usage  Free Use% Mountpoint 
/dev/sda4              79G   30G   46G  39% /home
```

But ```
sudo baobab
``` just shows 5 GB usage of /home.

Where did the 25 GB go?? I couldn´t find them with tools like
```
sudo du | sort 
```.

-- I had a problem like that before, when Space went to nirvana, but that was different: There were huge Backup-Files in a directory that was used as a mountpoint for another disk. So in the filesystem these files could not be seen.
But in this case there is no mount-point in /home!

Any Idea?

---

### Post by geirha on 2008-11-05
Try this command:
```
sudo du -m -x --max-depth=1 /home/* | sort -g
```

---

