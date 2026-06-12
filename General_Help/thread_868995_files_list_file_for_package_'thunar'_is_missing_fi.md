---
title: "files list file for package 'thunar' is missing final newline"
date: 2008-07-24
forum: General Help
---

### Post by exquest on 2008-07-24
yesterday my computer started acting up.  Programs started just crashing (the windows just started closing with no warning) a seemingly random lengths of time.  I saw there was an update available so I tried to start the update manager, which crashed. 

 At this point I restarted my computer and everything seemed to be OK but when I tried to run the update manager I get: An error occured and the following details are provided: E: /var/cache/apt/archives/ufw_0.16.2.2_all.deb: files list file for package `thunar' is missing final newline

When I try to do an apt-get install I get:

 files list file for package `thunar' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/khelpcenter_4%3a3.5.9-0ubuntu7.2_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)


Anyone have any ideas.  I'm stuck unable to update or install anything.:confused:

---

### Post by mali2297 on 2008-07-26
Try
```

sudo apt-get clean

```

---

### Post by exquest on 2008-07-26
I still get the same error

---

### Post by mali2297 on 2008-07-26
Try
```

sudo dpkg --configure -a

```

If that doesn't work, you could try to manually clean the cache:
```

sudo rm -v /var/cache/apt/archives/*

```
It should be safe to remove things in /var/cache.

---

