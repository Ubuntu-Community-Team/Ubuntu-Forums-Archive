---
title: "Copying / Migrating Ubuntu 8.04.1 LTS Server Desktop Environment (GNOME)"
date: 2009-01-07
forum: Installation &amp; Upgrades
---

### Post by dmfh on 2009-01-07
Folks:

I've got a pair of hosts I have running 8.04.1 LTS (Server) that also have the GNOME environment running & working on them. The hosts replicate some user data between them using rsync, and I recently expanded this to replicate the /home directory tree between the machines. As the machines have a single user, I figured this was a cool way to also replicate the GNOME environment.

Oddly, with the whole directory tree in /home really copied over to the second machine? Every application in GNOME hangs and will not launch on that box - including terminal. I'm thinking maybe there's some host specific stuff in the user home directory that shouldn't be copied, or needs changing. Any ideas?

So, what I also know for sure, and have made sure of to eliminate potential problems:

- The passwd / group files match with UIDs / GIDs between the machines.
- The whole /home directory, including . directories, files, etc. is being replicated.
- The GNOME on the copy machine launches with the GNOME widgets / setup it should have.

---

