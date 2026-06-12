---
title: "cant see contents of dvd"
date: 2010-05-10
forum: Hardware
---

### Post by nerdy_kid on 2010-05-10
hi i burned this a data dvd of a bunch of old .avi videos i had.  Think i burned it using linux but can't remember.  Anyway, i can't see the contents of this disk when it is mounted, either with ls -a or dolphin.  However if i access it with a windows VM i can see all the files.  any ideas?  Other dvd's work fine, its just this one that i cant see.  ubuntu lucid

---

### Post by mennowo on 2010-05-10
Is it possible the dvd was burnt using a not so common file system? Maybe you can check this in your VM windows? Then, using mount with a specified kind of file system to mount the dvd, maybe this enables access to the files in Ubuntu Lucid?

---

### Post by nerdy_kid on 2010-05-10
ok i have a ton of entries in syslog saying
```

2010-05-10 13:53:14	my-laptop	kernel	[31889.550732] VFS: busy inodes on changed media or resized disk sr0

```

it is a udf file system, i have a vista disk that is also udf and it works fine.  I'm going to a reboot and see if that helps.

---

### Post by nerdy_kid on 2010-05-10
ok strange, i started the xp vm up, and shut it down and after that dolphin showed all the files.  strange.  anyway, this is solved :)

---

