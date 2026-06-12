---
title: "groups, gid and user management"
date: 2008-10-26
forum: General Help
---

### Post by klas_katt on 2008-10-26
I'd like info on ALL groups. How do they work, what do they mean?

example:
adm, dialout, cdrom, floppy, audio, dip, video, plugdev, fuse, lpadmin, admin

I think floppy means I'm allowed to use a floppy (not installed).

Is there any documentation on basics like this (can't find anything useful on anything in debian) or do I have to post and post and post again?

---

### Post by bodhi.zazen on 2008-10-26
I understand, most of these groups are system users, and I had difficulty finding a good link.

Most of the groups fall into two categories, some are obvious.

Groups like "cdrom" give access to the cdrom, then there is audio, etc.

The other groups are in general named for the application that runs as a daemon.

mail for example is your mail server :)

In the absence of a specific link, do a google search on each group. I guess over time as you get more experience you get a sense of what most of these things are.

See also System -> Administration -> Services

---

### Post by klas_katt on 2008-10-28
Ok, maybe I have to settle with that :)

---

