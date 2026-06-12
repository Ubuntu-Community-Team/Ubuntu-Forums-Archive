---
title: "All out of space"
date: 2008-11-26
forum: General Help
---

### Post by Burb on 2008-11-26
I'm running 7.10 (now under xfce) and today I left a torrent running, when I came back I found it had completely filled all available space, so I deleted it as well as about 10gb of other files. However, the filesystem still reads as having 0kb of space. I've checked the deleted items folder and nothing is there. Can anyone tell what has happened and what I need to do? I can still log in just fine.

Thanks.

---

### Post by geirha on 2008-11-26
If some program has the files you deleted open still, the data in the files are still available. Close all programs that may have those files open (torrent application perhaps?), and the space should be reclaimed.

---

### Post by Burb on 2008-11-26
> **geirha said:**
> If some program has the files you deleted open still, the data in the files are still available. Close all programs that may have those files open (torrent application perhaps?), and the space should be reclaimed.

Done that already. Also restarted the computer and logged in with a new session. No change.

---

### Post by philinux on 2008-11-26
What does this command spit out.

```
df -h
```

---

### Post by Burb on 2008-11-26
> **philinux said:**
> What does this command spit out.

```
df -h
```

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              36G   34G     0 100% /
varrun                248M   92K  248M   1% /var/run
varlock               248M     0  248M   0% /var/lock
udev                  248M   60K  248M   1% /dev
devshm                248M     0  248M   0% /dev/shm
lrm                   248M   34M  214M  14% /lib/modules/2.6.22-15-generic/volatile
overflow              1.0M   68K  956K   7% /tmp

```

---

### Post by geirha on 2008-11-26
Sure you deleted the files as opposed to moved them to trash?

Try ```
sudo du -x -h --max-depth=1 /
``` to see where the space on / is used

---

### Post by Burb on 2008-11-26
Right, looks like it's in my home folder. I did move the files to the trash, but the trash is empty. So what's up?

---

### Post by geirha on 2008-11-26
Sounds a bit odd. Keep running that command, changing the path to the largest, until you find the files to delete.

```
sudo du -h -x --max-depth=1 $HOME
sudo du -h -x --max-depth=1 $HOME/.local    # if .local is taking up alot of space (Trash is inside there, .local/share/Trash)

```

---

### Post by Burb on 2008-11-26
Done the trick; thank you!

---

### Post by ibuclaw on 2008-11-26
Haha... nice one :)

Remember, when you press delete, you need to empty the trash can in order to unlink the files and free up space on your hard drive ;)

OK, peptalk over.
Happy Ubuntu'ing.

Regards
Iain

---

