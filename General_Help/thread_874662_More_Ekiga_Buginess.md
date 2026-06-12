---
title: "More Ekiga Buginess"
date: 2008-07-30
forum: General Help
---

### Post by Mark76 on 2008-07-30
Ever time I start it up I get the following two messages

> **Error while starting the listener for the SIP protocol**

You will not be able to receive incoming SIP calls. Please check that no other program is already running on the port used by Ekiga.

And

> **Error while starting the listener for the H.323 protocol**

You will not be able to receive incoming H.323 calls. Please check that no other program is alrerady running on the port used by Ekiga.

I'm pretty sure there's nothing else using those ports (does my web browser use the ports Ekiga uses?). But how can I make sure and what do I do to shut the offending software down, if it's nothing vital?

---

### Post by Mark76 on 2008-07-31
Will please tell me why it gives me this crap?

What am I supposed to do? Only run the stupid thing from a freaking command line without logging in to X first?

---

### Post by Mark76 on 2008-07-31
Okay. I managed to calm down enough to try running it from the terminal.  Here's the output

> ekiga-gtkonly

(ekiga-gtkonly:7128): Gtk-WARNING **: Theme directory 1256x256/apps of theme crystalproject has no size field


** (ekiga-gtkonly:7128): CRITICAL **: entry_get_bool: assertion `entry->type == GM_CONF_BOOL' failed

** (ekiga-gtkonly:7128): CRITICAL **: entry_get_bool: assertion `entry->type == GM_CONF_BOOL' failed

** (ekiga-gtkonly:7128): CRITICAL **: entry_get_int: assertion `entry->type == GM_CONF_INT' failed

** (ekiga-gtkonly:7128): CRITICAL **: entry_get_bool: assertion `entry->type == GM_CONF_BOOL' failed

** (ekiga-gtkonly:7128): CRITICAL **: entry_get_string: assertion `entry->type == GM_CONF_STRING' failed

(ekiga-gtkonly:7128): GLib-CRITICAL **: g_path_is_absolute: assertion `file_name != NULL' failed

** (ekiga-gtkonly:7128): CRITICAL **: entry_get_string: assertion `entry->type == GM_CONF_STRING' failed


Damn it. It's _not_ cool.

---

### Post by skralljt on 2008-12-21
I solved this problem by typing "sudo /etc/init.d/asterisk stop"
on the commandline.  When I started ekiga up it detected my accounts, I received a call from an old friend, called my parents, all was well.  Hope it helps!

---

