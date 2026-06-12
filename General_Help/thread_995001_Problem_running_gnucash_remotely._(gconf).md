---
title: "Problem running gnucash remotely. (gconf?)"
date: 2008-11-27
forum: General Help
---

### Post by aperomsik on 2008-11-27
I've got a home server and a laptop both running Intrepid. My gnucash data lives on the server. For years when I want to enter receipts from my bedroom I would run...

ssh -X server gnucash

and it would work fine. But since the server upgraded to Intrepid, it usually doesn't work. I get a dialog saying gnucash couldn't find its settings. 

If I run "ssh -X server" and then run gnucash from the prompt, it still doesn't work, and in the terminal I see messages like these:
[INDENT]
Failed to load key /apps/gnucash/general/show_splash_screen: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-NZVBImeOKn: Connection refused)
[/INDENT]
If I am sitting downstairs by the server machine, logged in to GNOME, and I run gnucash, it works fine.

Any ideas?

---

### Post by aperomsik on 2008-12-17
Seems to have something to do with gconf arguing with dbus and losing. After a few more rounds of googling I found a post which referred to the directory "~/.dbus/session-bus/" . After deleting all files in that directory under my home on the server, I can launch gnucash remotely again via ssh.

Time will tell whether that was a one-time corruption or whether it will be a recurring problem.

---

