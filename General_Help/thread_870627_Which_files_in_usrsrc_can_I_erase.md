---
title: "Which files in usr/src/ can I erase?"
date: 2008-07-26
forum: General Help
---

### Post by santiagorf on 2008-07-26
I've been using Disk Usage Analizer in order to see where I can free some space in my hard disk, and I have found that the usr/src/ folder has almost 1Gb used with the following files:


[HTML]-rw-r--r--  1 root src    322890 2008-05-14 12:46 alsa-modules-2.6.25_1.0.16-0ubuntu4+386_i386.deb
-rw-r--r--  1 root src    322914 2008-05-14 17:40 alsa-modules-2.6.251_1.0.16-0ubuntu4+386_i386.deb
-rw-r--r--  1 root src    321736 2008-05-16 16:17 alsa-modules-2.6.252_1.0.16-0ubuntu4+3ravas_i386.deb
-rw-r--r--  1 root src    321728 2008-05-17 00:43 alsa-modules-2.6.253_1.0.16-0ubuntu4+386_i386.deb
lrwxrwxrwx  1 root src        21 2008-05-17 12:39 linux -> /usr/src/linux-2.6.25
drwxr-xr-x 23 root root     4096 2008-05-17 17:36 linux-2.6.25
-rw-r--r--  1 root src  48601689 2008-04-16 23:13 linux-2.6.25.tar.bz2
drwxr-xr-x 20 root root     4096 2008-06-29 03:46 linux-headers-2.6.25
drwxr-xr-x 20 root root     4096 2008-05-17 00:27 linux-headers-2.6.251
-rw-r--r--  1 root src   9179584 2008-05-14 17:09 linux-headers-2.6.251_386_i386.deb
drwxr-xr-x 20 root root     4096 2008-05-17 00:27 linux-headers-2.6.252
-rw-r--r--  1 root src   9107090 2008-05-16 16:15 linux-headers-2.6.252_3ravas_i386.deb
drwxr-xr-x 20 root root     4096 2008-05-17 00:27 linux-headers-2.6.253
-rw-r--r--  1 root src   9127214 2008-05-16 18:03 linux-headers-2.6.253_386_i386.deb
-rw-r--r--  1 root src   9185992 2008-05-14 05:52 linux-headers-2.6.25_386_i386.deb
-rw-r--r--  1 root src  19578282 2008-05-14 17:01 linux-image-2.6.251_386_i386.deb
-rw-r--r--  1 root src  13423356 2008-05-16 16:08 linux-image-2.6.252_3ravas_i386.deb
-rw-r--r--  1 root src  14593308 2008-05-16 17:57 linux-image-2.6.253_386_i386.deb
-rw-r--r--  1 root src  19809376 2008-05-14 05:32 linux-image-2.6.25_386_i386.deb
drwxrwsr-x  3 root src      4096 2008-03-08 21:24 modules[/HTML]

I have compiled the kernel several times, and the only version I need is 2.6.253. However, since I'm new on this, I have no idea which files are necessary and which are not.
Does anyone can tell what directory/files I can earase?

Thanks in advance
Santiagorf

---

### Post by iaculallad on 2008-07-26
If you're not sure of what to erase, just leave it that be since your /usr directory contains applications, libraries, documentation etc. for all of you're user-related programs.

Instead, to get more of free spaces, try the following commands below:

```
sudo apt-get clean
sudo apt-get autoclean
```

Sure you could delete the /usr/src/linux-2.6.25 directory.

---

### Post by santiagorf on 2008-07-26
thanks!! and in fact it is the heaviest directory

---

