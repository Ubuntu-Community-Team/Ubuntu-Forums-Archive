---
title: "locate misses some files"
date: 2005-11-04
forum: General Help
---

### Post by jimmyp on 2005-11-04
I can run locate on files in my home directory and on my windows partition and it usually finds them ok.  It doesn't work all the time though.  I have a movies directory on my windows partition and locate doesn't see the files in that directory:

HOST:~$ ls -ld /windows/movies
drwxr-xr-x  2 root root 32768 2005-10-29 10:57 /windows/movies/
HOST:~$ ls -l /windows/movies
total 3463104
-rwxr-xr-x  1 root root 686133028 2005-07-12 19:32 collateral.avi*
-rwxr-xr-x  1 root root         0 2005-10-29 10:57 fat*
-rwxr-xr-x  1 root root 722987096 2005-06-09 08:27 mean_girls.avi*
-rwxr-xr-x  1 root root 725573554 2005-08-17 18:15 mononoke.avi*
-rwxr-xr-x  1 root root 687952690 2005-08-11 19:06 napolean_dynamite.avi*
-rwxr-xr-x  1 root root 723502176 2005-06-16 22:58 oceans_twelve.avi*
HOST:~$ locate napolean_dynamite.avi
HOST:~$

How do I make locate see those files?

---

### Post by aclaunch on 2005-11-04
Have you added the files/directory recently? Locate updates its database, I think daily (via cron) and until this happens locate will miss newly added files. You can run "sudo updatedb" to force an update earlier than the routine cron job.

Good Luck,
Alan

---

### Post by jimmyp on 2005-11-04
[QUOTE=aclaunch]Have you added the files/directory recently? Locate updates its database, I think daily (via cron) and until this happens locate will miss newly added files. You can run "sudo updatedb" to force an update earlier than the routine cron job.

Good Luck,
Alan[/QUOTE]

I forgot to say that the files have been there for a while.  Running updatedb by hand doesn't fix it.

---

### Post by grinchy on 2005-11-04
i usually run sudo alocate -u
or it could be slocate i can't remember

---

### Post by jimmyp on 2005-11-07
[QUOTE=grinchy]i usually run sudo alocate -u
or it could be slocate i can't remember[/QUOTE]

I gave that a shot and it still didn't find the files... looks like time for a bug report.

---

### Post by poptones on 2005-11-07
It's likely not a bug but a feature. Check /etc/updatedb.conf and see what sort of exclusions you have. 

```
# filesystems which are pruned from updatedb database
PRUNEFS="NFS nfs afs proc smbfs autofs iso9660 ncpfs coda devpts ftpfs devfs mfs sysfs"

```

---

### Post by jimmyp on 2005-11-09
locate sees other files on the same partition.  If that partition was being excluded then locate would not report any files from it.  It is only certain files on my windows partition that don't show up.

---

### Post by Kyral on 2005-11-09
You could try running Beagle instead. Thing is hyper when it comes to indexing files

---

### Post by McQuaid on 2006-02-01
I just want to report that I as well get this with certain files.  Yes the dirs are included and some turn up others don't.  Anyone else have info on why locate fails in finding some files?

---

