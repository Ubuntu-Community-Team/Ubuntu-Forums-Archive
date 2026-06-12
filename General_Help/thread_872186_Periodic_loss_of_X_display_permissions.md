---
title: "Periodic loss of X display permissions"
date: 2008-07-27
forum: General Help
---

### Post by shirsch on 2008-07-27
I've just started seeing this on Kubuntu 8.04.1, and it's VERY annoying.  Periodically, I seem to lose permission to connect to my own desktop.  For example, trying to start xclock from a terminal gets this:

No protocol specified
Error: Can't open display: :0

If I do:

$ xhost +my_machine
$ xhost -

Everything is fine again.  My home directory is mounted over NFS, and I've seen other reports of problems in this type of situation.

Any advice appreciated!

---

