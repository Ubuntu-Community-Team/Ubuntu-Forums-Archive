---
title: "unable to install/upgrade anything"
date: 2009-09-24
forum: Installation &amp; Upgrades
---

### Post by Dakanya on 2009-09-24
I've been unable to update my jaunty and I also haven't been able to install any packages.

In both instances they have this error in common
```
(Reading database ... dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd): files list for package `gdebi': Input/output error
```

When trying to use the upgrade manager I get the following:
```
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd): files list for package `gdebi': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
```

When attempting to install a .deb file I get:
```
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline
Selecting previously deselected package python-sip4.
(Reading database ... dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd): files list for package `gdebi': Input/output error
gdebi-gtk: Fatal IO error 9 (Bad file descriptor) on X server :0.0.
Selecting previously deselected package anki.
(Reading database ... dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd): files list for package `gdebi': Input/output error
```

---

### Post by Partyboi2 on 2009-09-24
Try moving the list file out of the way first, then reinstalling gdebi.
```
sudo mv  /var/lib/dpkg/info/gdebi.list /var/lib/dpkg/info/gdebi.list.broke
``````
sudo apt-get clean
sudo apt-get --reinstall install gdebi
sudo dpkg --configure -a
```

---

### Post by khelben1979 on 2009-09-24
Post your output from ```
sudo df -h
```

If you don't have enough disk space, you're not able to install anything. Of course there could be something else as well, but we'll see that later.

---

### Post by Dakanya on 2009-09-24
@Partyboi2: Reinstalling gdebi was unsuccessful. I got the following:

```
sudo apt-get --reinstall install gdebi
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 43 not upgraded.
1 not fully installed or removed.
Need to get 33.2kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main gdebi 0.4.9 [33.2kB]
Fetched 33.2kB in 0s (41.4kB/s)
(Reading database ... 
dpkg: serious warning: files list file for package `gdebi' missing, assuming package has no files currently installed.
231353 files and directories currently installed.)
Preparing to replace gdebi 0.4.9 (using .../archives/gdebi_0.4.9_all.deb) ...
pycentral: pycentral pkgremove: package gdebi is not installed
pycentral pkgremove: package gdebi is not installed
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
pycentral: pycentral pkgremove: package gdebi is not installed
pycentral pkgremove: package gdebi is not installed
dpkg: error processing /var/cache/apt/archives/gdebi_0.4.9_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
pycentral: pycentral pkginstall: package gdebi is not installed
pycentral pkginstall: package gdebi is not installed
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/gdebi_0.4.9_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


@khelben1979 Admittedly my disk space is low but at the moment 1gb should be more than enough.

```
sudo df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             9.2G  7.7G  1.1G  89% /
tmpfs                 1.3G     0  1.3G   0% /lib/init/rw
varrun                1.3G  348K  1.3G   1% /var/run
varlock               1.3G     0  1.3G   0% /var/lock
udev                  1.3G  168K  1.3G   1% /dev
tmpfs                 1.3G  200K  1.3G   1% /dev/shm
lrm                   1.3G  2.2M  1.3G   1% /lib/modules/2.6.28-15-generic/volatile
/dev/sda1             177G  173G  3.9G  98% /mnt/windows
```

Thanks for the assistance, I really appreciate it guys.

---

### Post by khelben1979 on 2009-09-24
I can't even see that you have an /home partition from that list, not good.

You should take a look at [this document]("http://tldp.org/HOWTO/Partition/requirements.html#AEN493") on how to partition the harddrive. At the same time I suspect that you haven't done anything wrong when you chose to partition the harddrive in the first place, it's just that by the old way of partitioning up the harddrive it was suggested to use several partitions and I always stick to this because it never gives me any problems.

---

### Post by Dakanya on 2009-09-24
> **khelben1979 said:**
> I can't even see that you have an /home partition from that list, not good.

You should take a look at [this document]("http://tldp.org/HOWTO/Partition/requirements.html#AEN493") on how to partition the harddrive. At the same time I suspect that you haven't done anything wrong when you chose to partition the harddrive in the first place, it's just that by the old way of partitioning up the harddrive it was suggested to use several partitions and I always stick to this because it never gives me any problems.

Thanks for the link! I haven't gotten around to setting up partitions yet. I am currently in the middle of cleaning out my Windows partition so I can expand my Ubuntu partition.

---

### Post by arrange on 2009-09-24
Could you post the contents of the */var/lib/dpkg/info/gdebi.list.broke* file? (If it's not all rubbish.)

---

### Post by Dakanya on 2009-09-24
@arrange I was unsuccessful in opening the file.

** (gedit:8909): WARNING **: Hit unhandled case 0 (I/O error) in parse_error.

---

### Post by arrange on 2009-09-24
I would just remove the */var/lib/dpkg/info/gdebi.prerm* file, then run *apt-get -f install*```

sudo mv /var/lib/dpkg/info/gdebi.prerm /var/lib/dpkg/info/gdebi.prerm.old
sudo apt-get -f install
```

---

### Post by Dakanya on 2009-09-24
@arrange The solution you suggested solved my problem! Thanks a lot for your assistance.

---

