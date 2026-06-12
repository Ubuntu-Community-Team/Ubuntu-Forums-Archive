---
title: "GNUMP3d in Launchpad but not in Universe? (Intrepid 8.10)"
date: 2008-11-24
forum: General Help
---

### Post by Sir_Brizz on 2008-11-24
Hi guys,

I've had GNUMP3d installed on my server for ages through apt, however as of updating to Intrepid, dpkg reported it as broken. It wouldn't let me uninstall/reinstall it, so I purged it and then it could not be found through apt-cache. I have Unverse and Multiverse enabled, and Launchpad shows the package in Universe, however it doesn't come up in search and it won't install from there. I ended up just installing it manually with the .deb, which worked fine.

So I just wanted to post that here for people who are wondering what is going on. I wasn't sure where else to put it or report it.

[https://launchpad.net/ubuntu/intrepid/i386/gnump3d/3.0-2](https://launchpad.net/ubuntu/intrepid/i386/gnump3d/3.0-2)

---

### Post by vanstrien on 2008-12-15
I've run into this same issue.  Anyone heard of why it went away?  It has an earlier entry in Launchpad for Intrepid but then the most recent entry says it isn't in Intrepid anymore.  What's gives?

---

### Post by killermist on 2008-12-20
Was able to install from the .deb (thanks for the link Sir_Brizz).
But now I have the problem of as it runs, it continues to forget everything it knows about the collection.
As suggested in other reading material, I'm using symlinks from private users home directories into /var/music/"username"
(sudo ln -s /home/"username"/music /var/music/"username")

Does anyone know if there's some file or directory that the server's user is supposed to have read/write access to so it can store it's previously indexed information about the collection?

I did notice
```

$ ll /var/cache/gnump3d/
total 4.0K
drwxr-xr-x 2 gnump3d nogroup 4.0K 2007-10-29 15:10 serving
-rw-r--r-- 1 root    root       0 2008-12-20 00:50 song.tags
```

Which I chowned to gnump3d (the default server user, which I retained).
But come to think of it, I may bot have restarted the server after, so it may have encountered it as unwritable and remembered to not try to write anything.

Ah.  Well that explains it.  Restarted the server, and on server restart, it appears it runs the indexer, which ran successfully this time instead of silently failing.

---

