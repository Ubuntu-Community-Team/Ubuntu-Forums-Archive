---
title: "Suspend locks screen, can I avoid this?"
date: 2008-11-28
forum: Hardware
---

### Post by oreomike on 2008-11-28
Running Hardy Heron, and I have configured Gnome to auto-log in as my account.  This works great on boot, but when I suspend or hibernate, it requires a password to log back in when I resume.

Is there a configurable way, or a pointer to source code I can modify, that can help me start the computer always without a password?

---

### Post by sdennie on 2008-11-28
Hit Alt-F2 and type gconf-editor.  Navigate to /apps/gnome-power-manager/lock and uncheck suspend and hibernate.

---

### Post by rmaraujo on 2009-02-19
Just an addition that made me waste some time. Do NOT run gconf-editor using sudo. Otherwise, it will set the locks for the root, not the user, and Ubuntu will keep asking for the password when waking-up.

Simple thing, but we get so used at using command line configurations with sudo...

Ricardo

---

