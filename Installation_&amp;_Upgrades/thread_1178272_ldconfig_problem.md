---
title: "ldconfig problem"
date: 2009-06-04
forum: Installation &amp; Upgrades
---

### Post by nedkelly on 2009-06-04
When I install something I get this error

```
 /sbin/ldconfig.real: /usr/local/lib/ is not a symbolic link
```

I get the same error if I do "sudo ldconfig"

The only thread I can find with the same problem is [http://ubuntuforums.org/showthread.php?t=1008568]("http://ubuntuforums.org/showthread.php?t=1008568")

And it does not seem as the same problem. Since I do not have "libANN_char.so" or anything with a different permissions

Can anyone help?

```
nedkelly@ubuntu:~$ ls -l /usr/local
total 36
drwxr-xr-x  2 root root 4096 2009-06-03 15:57 bin
drwxr-xr-x  2 root root 4096 2009-03-20 20:54 etc
drwxr-xr-x  2 root root 4096 2009-03-20 20:54 games
drwxr-xr-x  2 root root 4096 2009-03-20 20:54 include
drwxr-xr-x  7 root root 4096 2009-06-03 15:57 lib
drwxr-xr-x  4 root root 4096 2009-04-24 01:50 Livestation
lrwxrwxrwx  1 root root    9 2009-03-20 20:54 man -> share/man
drwxr-xr-x  2 root root 4096 2009-03-20 20:54 sbin
drwxr-xr-x 13 root root 4096 2009-06-04 15:09 share
drwxr-xr-x  2 root root 4096 2009-03-20 20:54 src
nedkelly@ubuntu:~$ ls -l /usr/local/lib
total 5880
drwxr-xr-x 2 root root     4096 2009-03-26 00:39 codecs
-rw-r--r-- 1 root root      890 2009-06-03 16:01 libspotify.la
-rwxr-xr-x 1 root root  1990688 2009-06-03 16:01 libspotify.so
-rwxr-xr-x 1 root root  1990688 2009-06-03 16:01 libspotify.so.1
-rwxr-xr-x 1 root root  1990688 2009-06-03 16:01 libspotify.so.1.0.45211
drwxrwsr-x 3 root staff    4096 2009-05-23 20:39 ocaml
drwxrwsr-x 3 root staff    4096 2009-04-28 19:47 python2.5
drwxrwsr-x 4 root staff    4096 2009-04-28 19:44 python2.6
drwxr-xr-x 3 root root     4096 2009-04-29 00:55 site_ruby
```

---

