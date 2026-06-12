---
title: "Brutal system Hang"
date: 2008-08-30
forum: General Help
---

### Post by ixlam on 2008-08-30
I'm using 8.04 on 32 bit machine all Up-To-Date,, . that now hangs after log-in on all applications, firestarter etc.

After log-in any and all applications, even nautilus, takes a very long time to open.

"Sudo firesterter" doesn't even start AT ALL,  but shows as "sleeping" in gnome-system-monitor (which also takes EONS to start up)

How can I diagnose whats causing this?

(as always thanks to anyone with suggestions)

---

### Post by sdennie on 2008-08-31
What is the output of:

```

cat /etc/hosts

```

Also, you could bring up a terminal and type:

```

tail -f /var/log/syslog

```

Then open applications and see if anything appears in the terminal.  That may or may not be useful.

---

