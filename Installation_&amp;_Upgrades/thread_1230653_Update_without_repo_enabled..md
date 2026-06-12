---
title: "Update without repo enabled."
date: 2009-08-03
forum: Installation &amp; Upgrades
---

### Post by hellmet on 2009-08-03
I was wondering if there was a way to :
1) Install a particular software, say firefox
2) Remove its repo from sources.list
3) Still be able to update that particular software when an update is available.

The reason for this is that having repos enabled takes up quite some space on the hard-drive and on a thin-client, it is very precious.

Thanks for your time!

---

### Post by Partyboi2 on 2009-08-03
Hi, one way is to add the 3rd party repo to your sources.list (System>Admin>Software Sources>Third Party Software) then install the program you want, then disable the repo and every so often re-enable the repo to check for updates.

---

### Post by hellmet on 2009-08-03
I don't think an end-user would want or be able to do that each time.

---

### Post by Sef on 2009-08-04
I would use the [Ubuntu FireFox PPA]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa").

---

### Post by slakkie on 2009-08-04
Takes a lot of space?

/var/cache/apt is 24 Mb big.. 

```

8:44 pts/1 1 wesleys@eniac:/var/cache/apt$ du -sh
1.5M    .                                        
8:44 pts/1 0 wesleys@eniac:/var/cache/apt$ sudo mv /etc/apt/sources.list.ORIG /etc/apt/sources.list
8:44 pts/1 0 wesleys@eniac:/var/cache/apt$ sudo aptitude update                                    
Writing extended state information... Done                                                         
Hit http://nl.archive.ubuntu.com jaunty Release.gpg                                                
...
...
Hit http://nl.archive.ubuntu.com jaunty-backports/multiverse Sources
Reading package lists... Done

8:44 pts/1 0 wesleys@eniac:/var/cache/apt$ du -sh
24M     .
8:44 pts/1 0 wesleys@eniac:/var/cache/apt$ lt
total 24352
drwxr-xr-x 3 root root   249856 2009-08-04 08:41 archives
-rw-r--r-- 1 root root 12317739 2009-08-04 08:44 srcpkgcache.bin
-rw-r--r-- 1 root root 12407553 2009-08-04 08:44 pkgcache.bin
8:44 pts/1 0 wesleys@eniac:/var/cache/apt$

```

I don't see how that is much space..

---

### Post by hellmet on 2009-08-04
It is a lot of space on a thin client with 512MB space. I clearly mentioned that in my original post.

---

### Post by slakkie on 2009-08-04
Write a script that does the following (as root):

```

cp /etc/apt/sources.list.defined /etc/sources.list
aptitude update && aptitude safe-upgrade
aptitude clean
:> /etc/apt/sources.list
aptitude update

```

Run that on a $period basis and you can upgrade when you want, using some space when needed, removing it afterward..

ps. you did not mention you only had 512 Mb to spare. Thin clients do not mean a piece of paper as diskspace.

---

