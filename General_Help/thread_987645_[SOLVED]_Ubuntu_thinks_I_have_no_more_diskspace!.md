---
title: "[SOLVED] Ubuntu thinks I have no more diskspace!"
date: 2008-11-19
forum: General Help
---

### Post by 4Play on 2008-11-19
Hello, ever since Vmware Workstation 6.5 started giving me an error about not having enough space on the /tmp folder, most things I do that require files to be written to the / partition (my /home is on a separate partition) gives me a "not enough disk space" error.
Strangely enough, I can install apps with apt-get install (so i guess /usr/bin and /bin are not "full") but even then, I get error messages during the install telling me it couldn't create the man pages because there is not enough free space on disk.

here is the output of df -h
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7             9.7G  5.4G  3.9G  59% /
tmpfs                 2.0G     0  2.0G   0% /lib/init/rw
varrun                2.0G  276K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  2.9M  2.0G   1% /dev
tmpfs                 2.0G  292K  2.0G   1% /dev/shm
lrm                   2.0G  2.4M  2.0G   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sda8             102G   39G   59G  40% /home
overflow              1.0M  984K   40K  97% /tmp

```

Nothing there is close to 100% usage. I am rather clueless as to the approach I should take to this problem...I mean how can i tell it that there *is* plenty of free space when the system thinks there isn't?

any help would be much appreciated.
Thanks :)

edit: Running Intrepid Ibex with all updates applied, have removed VMware workstation (am using vmware player for now)

edit2: i just saw the "overflow" line with the /tmp mount point at 97%...cant believe i didnt see that before....seems like ubuntu is mounting /tmp to RAM (and only 1MB!!) and not to the / filesystem like I expected....but this probably isnt too hard to solve...sorry for the stupid thread :p

---

### Post by drs305 on 2008-11-19
Glad to see you figured it out for yourself. Please mark the thread 'Solved' via the Thread Tools link at the top right of the original post so the helpers can skip this one and move on to unresolved issues. Thanks.

---

