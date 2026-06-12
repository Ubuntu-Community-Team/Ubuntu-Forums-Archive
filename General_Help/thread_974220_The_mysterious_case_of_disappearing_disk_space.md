---
title: "The mysterious case of disappearing disk space"
date: 2008-11-07
forum: General Help
---

### Post by nikidinsey on 2008-11-07
Hi all,

Check this.. 

I'm in gksu nautilus hanging out in root working with lampp on an external server.

One day I notice I have very little disk space left (30Mb) so I try to open Trash in nautilus and get an error along the likes of "Sorry, operation not supported".

After surfing the interwebs for "over 9000 hours" I finally find that for some reason the trash folder that was/normally is stored in /root/.Trash actually resides in  ~/.local/share/Trash/

Anyway, after finding the right dir I deleted the files in the data and info folders and all the space returned.. Well done you say, n00b works it out for himself? well check this, because this is where it gets interesting.......................................

So in gksu root nautilus, I go to my main user home (/home/admin), into the torrents folder and delete a 6Gb film. The space doesn't show as free (as expected), the film doesn't show in either root's or admin's  ~/.local/share/Trash/ folder either!

So now my server has at least 6Gb of space that has disappeared with no way of me reclaiming it!

What is going on!?!

In before:  "hey I tried that on my machine and the file turns up in my roots trash folder as expected"

I think this might have something to do with the partitioning on my server here's the df -h

```
Filesystem            Size  Used Avail Use% Mounted on
rootfs                5.0G  3.6G  1.2G  76% /
/dev/root             5.0G  3.6G  1.2G  76% /
tmpfs                 2.0G   92K  2.0G   1% /var/run
tmpfs                 2.0G     0  2.0G   0% /var/lock
/dev/root             5.0G  3.6G  1.2G  76% /dev/.static/dev
udev                  2.0G   20K  2.0G   1% /dev
tmpfs                 2.0G     0  2.0G   0% /dev/shm
tmpfs                 2.0G   92K  2.0G   1% /var/run
tmpfs                 2.0G     0  2.0G   0% /var/lock
/dev/sda2             683G  215G  434G  34% /home
```

_________

Any help greatly appreciated, thanks

niks

---

### Post by geirha on 2008-11-07
Is the torrent-program still open? If so, it might have that file you deleted still opened, and the file will still exist as long as a program has it open, even if it no longer has a filename. The space should come back as soon as all programs who had the file open has been exited.

To get a better overview of where the space is used inside a certain folder, try du. For example to check your homedir (~) ```
du -x -h --max-depth=1 ~
```

---

