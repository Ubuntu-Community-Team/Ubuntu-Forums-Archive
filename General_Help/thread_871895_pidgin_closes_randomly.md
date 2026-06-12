---
title: "pidgin closes randomly"
date: 2008-07-27
forum: General Help
---

### Post by Riffer on 2008-07-27
I've noticed that Pidgin will suddenly shut down on its own.  Its at random times and isn't dependent on any thing, it could be when its sitting idle or when I'm chatting.  Any ideas?

---

### Post by tsjhangra on 2008-07-28
I'm having the same issue... I've tried running Pidgin from terminal and it doesnt come up with any errors :S

It started last Thursday :(

Any ideas?

---

### Post by The Tronyx on 2008-07-28
This is happening with me as well, the output from my terminal is below.

```

tronyx@wrekx:~$ pidgin
**
** Gtk:ERROR:(/build/buildd/gtk+2.0-2.12.9/gtk/gtktreestore.c:531):gtk_tree_store_get_path: assertion failed: (G_NODE (iter->user_data)->parent != NULL)
Aborted
tronyx@wrekx:~$ 

```

---

### Post by c2olen on 2008-07-28
I had the same problem, but it started in 07.04.
My experience was it occured most when using a specific Yabber/XMMP session to a the dutch hyves chatservers. Once I disabled that account, it only happened occasionally. Still using another Jabber/XMMP session (GoogleChat) though. Maybe it relates to Jabber/XMMP sessions. 

Currently I am running a fully updated stable (08.04) version (2.4.1), and no crash so far...

It is mentioned several times on these forums
[http://ubuntuforums.org/showthread.php?t=664027](http://ubuntuforums.org/showthread.php?t=664027)
[http://ubuntuforums.org/showthread.php?t=692382](http://ubuntuforums.org/showthread.php?t=692382)

---

