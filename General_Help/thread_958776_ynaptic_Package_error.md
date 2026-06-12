---
title: "ynaptic Package error"
date: 2008-10-25
forum: General Help
---

### Post by the lemming on 2008-10-25
Wile I was getting the KDE packages the manager crashed.

Now when I try to start up the package manager I get the following error message.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


Any ideas how I can resolve this?

Cheers

---

### Post by fooman on 2008-10-25
open a terminal and type or copy/paste the following into it:

```
sudo dpkg --configure -a
```

---

### Post by the lemming on 2008-10-25
I tried your request and got the following from the terminal

dpkg: failed to write status record about `gnome-user-guide' to `/var/lib/dpkg/status': No space left on device


And when I got back into the synaptic I got

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


Any more sugetions?

---

### Post by loell on 2008-10-25
you've run out of space :(

how much space do you have in your drive?

---

### Post by drs305 on 2008-10-25
> **the lemming said:**
> 
dpkg: failed to write status record about `gnome-user-guide' to `/var/lib/dpkg/status': [COLOR="Red"]No space left on device[/COLOR]
Any more sugetions?

Is there a chance your partition is full? You can run this command to check:
```
df -h
```

If it is unexpectedly full, you might want to check the link in my signature line regarding finding and emptying trash bins.

---

### Post by the lemming on 2008-10-25
Here is a copy of df -h



Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             3.0G  3.0G     0 100% /
varrun                629M  220K  628M   1% /var/run
varlock               629M     0  629M   0% /var/lock
udev                  629M   48K  629M   1% /dev
devshm                629M   52K  628M   1% /dev/shm
lrm                   629M   39M  590M   7% /lib/modules/2.6.24-21-generic/volatile
/dev/sda3              37G  508M   34G   2% /home
overflow              1.0M   36K  988K   4% /tmp
gvfs-fuse-daemon      3.0G  3.0G     0 100% /home/frank/.gvfs





My laptop has an 75gb drive.  Half is allocated to XP and the rest to ubuntu.  I only installed ubuntu two day ago so I'm curious how ubuntu could have filled up 35gb of space?

---

### Post by drs305 on 2008-10-25
Your /dev/sda2 is showing 100%. Is sda2 your system (root) partition? It's only showing 3GB. Is that correct? I don't think you can get away with a 3 GB root partition unless you have done some kind of special install or have really limited the apps.

**Added:** You are only using 2% of your 34GB home partition. Are you familiar with the gparted partitioning tool? It looks like you need to expand your / partition, probably at the expense of /home.

---

### Post by bryonak on 2008-10-25
> **the lemming said:**
> 
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             3.0G  3.0G     0 100% /
/dev/sda3              37G  508M   34G   2% /home


```


You have two partitions for Ubuntu, one for the system, which is mounted as "/", and one for your user account, mounted as "/home", which is the equivalent to "Documents and settings" in Windows.
I don't know if this is done by default, though I highly doubt it, since it only uses one partition AFAIK.

As you can see from your file system table, only 3GB are assigned to your system partition, which is too little. It should have between 5 and 8 GB (or up to 10GB if you want to add a lot of alternative environments, developer tools, source headers, etc).

The home directory is meant for your personal use, apart from documents that means your music collection, movies, all the big personal stuff. But installed applications reside on the systems partition, which has run out of space on your install.
If you're comfortable editing the partitions (which you've probably done during the installation), try the gPartEd LiveCD in order to increase your system partition.
Otherwise the simplest, hassle-free method would be deleting those two partitions and reinstalling Ubuntu. Again with 2 partitions, which is [the recommended layout]("http://www.psychocats.net/ubuntu/partitioning"), but this time with a bigger system partition.

---

