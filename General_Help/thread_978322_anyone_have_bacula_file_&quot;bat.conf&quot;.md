---
title: "anyone have bacula file &quot;bat.conf&quot;"
date: 2008-11-11
forum: General Help
---

### Post by walter_j on 2008-11-11
I installed bacula and the bat program, but I get an error 
Config error: Cannot open config file "./bat.conf": No such file or directory

Does anyone have this file?

ps: the install also missed bacula-dir.conf too, but there is a sample file in the docs (but no bat.conf)

Walter

---

### Post by walter_j on 2008-11-14
bump

---

### Post by nijaba on 2009-08-15
The default bat.conf file is in /etc/bacula/bat.conf.

---

### Post by ve4cib on 2009-08-27
There's not much to bat.conf, really.  Here's what I use (with the director's name, IP address, and password all changed)

```

#
# Bacula Administration Tool (bat) configuration file
#

Director {
  Name = bacula-dir
  DIRport = 9101
  address = 0.0.0.0
  Password = "09i8OIJ2Alkjasd094LKAiw94jf02q"
}

```

---

