---
title: "Autofs isn't timing my autofs'es out..."
date: 2006-07-02
forum: Hardware &amp; Laptops
---

### Post by enigma_0Z on 2006-07-02
OK, here's my probelm.

I wrote an autofs script to mount device nodes. Now, autofs won't time out the mounts and unmount them. This is particularly important for thumb drives (the main purpose I wrote the script).

My script does work, here's the output of the command (it's proper autofs syntax)

```

$ /etc/auto.dev sda
 -fstype=auto,defaults :/dev/sda

```

And here's the contents of my auto.master file...

```

$ cat /etc/auto.master
#
# $Id: auto.master,v 1.4 2005/01/04 14:36:54 raven Exp $
#
# Sample auto.master file
# This is an automounter map and it has the following format
# key [ -mount-options-separated-by-comma ] location
# For details of the format look at autofs(5).
#/misc  /etc/auto.misc --timeout=60
#/smb   /etc/auto.smb
/mnt/auto/misc  /etc/auto.misc
/mnt/auto/net   /etc/auto.net
/mnt/auto/dev   /etc/auto.dev --timeout=10

```

Anyway, my questions are this:

1. Why isn't the timout option timing out when it's supposed to

2. How can I force autofs to unmount an item, even if it hasn't timed out (for instance, if I know that it's inactive)?

3. How can I tell if it's been umounted, I can just look at /etc/mtab and/or /proc/mounts, right?

Thanks.

---

