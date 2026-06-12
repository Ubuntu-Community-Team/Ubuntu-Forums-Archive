---
title: "Problem with Synaptic Package Manager"
date: 2008-07-18
forum: General Help
---

### Post by landcross on 2008-07-18
Problem with Synaptic Package Manager

I am in a loop going round in circles....  can anyone help?

In Synaptic
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

Try that in terminal and get

dpkg: too many errors, stopping

dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


I run that and get the same problem

---

### Post by drs305 on 2008-07-18
You are running the command with sudo, correct?
```
sudo dpkg --configure -a
```

---

### Post by Kevbert on 2008-07-18
Also run
```
sudo apt-get install -f
```
which will repair any damaged packages.

---

### Post by landcross on 2008-07-18
Thanks

But same message and loop with both commands


This seems to be the problem
 * Starting PostgreSQL 8.3 database server                                       * The PostgreSQL server failed to start. Please check the log output:
2008-07-18 17:41:51 BST LOG:  could not load root certificate file "root.crt": no SSL error reported
2008-07-18 17:41:51 BST DETAIL:  Will not verify client certificates.
2008-07-18 17:41:51 BST FATAL:  could not create shared memory segment: Invalid argument
2008-07-18 17:41:51 BST DETAIL:  Failed system call was shmget(key=5433001, size=38207488, 03600).
2008-07-18 17:41:51 BST HINT:  This error usually means that PostgreSQL's request for a shared memory segment exceeded your kernel's SHMMAX parameter.  You can either reduce the request size or reconfigure the kernel with larger SHMMAX.  To reduce the request size (currently 38207488 bytes), reduce PostgreSQL's shared_buffers parameter (currently 4096) and/or its max_connections parameter (currently 103).
	If the request size is already small, it's possible that it is less than your kernel's SHMMIN parameter, in which case raising the request size or reconfiguring SHMMIN is called for.
	The PostgreSQL documentation contains more information about shared memory configuration.
                                                                         [fail]
invoke-rc.d: initscript postgresql-8.3, action "start" failed.
dpkg: error processing postgresql-8.3 (--configure):
 subprocess post-installation script returned error exit status 1

---

### Post by Kevbert on 2008-07-18
This has occurred before.  Please take a look at [[COLOR="Red"]this[/COLOR]]("http://www.len.ro/work/tools/ubuntu-gutsy-on-a-dell-latitude-d820/the-painful-upgrade").  
[COLOR="Red"]If you know what package caused this you could try[/COLOR]
```
sudo apt-get remove --purge *package*
``` where *package* is the name of your problem package
[COLOR="Red"]Be very careful with this command as it could cause even more problems if you get the package name wrong or mistype anything.[/COLOR]
Good luck.

---

### Post by Helios1276 on 2008-07-18
I seem to be getting roughly the same problem as OP, so I figured to post here instead of a new thread. After a fresh install(Heron) and downloading all updates (dumb in retrospect), I'm getting "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report." whenever I try Synaptic or Enabling restricted ATI drivers.

helios@helios-laptop:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu39.1) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-19-generic
dpkg: subprocess post-installation script returned error exit status 1
helios@helios-laptop:~$

---

### Post by avtolle on 2008-07-18
Helios1276, your situation indicates that you are out of room on the partition. Please post the results of ```
df -h
```
Without that data, the above is a guess at best; also, if you have a separate boot partition, I'm guessing it might be full.

---

### Post by Helios1276 on 2008-07-18
Ya your right it seems,

helios@helios-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda8              30G  2.9G   25G  11% /
varrun                759M  104K  759M   1% /var/run
varlock               759M     0  759M   0% /var/lock
udev                  759M   68K  759M   1% /dev
devshm                759M   12K  759M   1% /dev/shm
lrm                   759M   39M  720M   6% /lib/modules/2.6.24-19-generic/volatile
/dev/sda7              46M   41M  2.9M  94% /boot
gvfs-fuse-daemon       30G  2.9G   25G  11% /home/helios/.gvfs
/dev/scd1             3.8M  3.8M     0 100% /media/cdrom1
/dev/sdb1             958M  791M  168M  83% /media/CleverStuff
helios@helios-laptop:~$ 

I must have missed a zero lol, whats the quickest fix would you say? a trip to the partitioner I suppose?

---

