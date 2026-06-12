---
title: "Help Please?"
date: 2008-08-20
forum: General Help
---

### Post by Pandyrenim on 2008-08-20
I'm Running Ubuntu 8.04

when i open up my update manager
or try to install anything i get this message


A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'http://security.ubuntu.com/ubuntu' is not known on line 53 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

i've looked at my source list, it looks fine... but i'm kinda new to this thing

---

### Post by pauper on 2008-08-20
Try commenting out line 53.

Check if that line is in fact as "[noparse]http://security.ubuntu.com/ubuntu[/noparse]" instead
of "deb [noparse]http://security.ubuntu.com/ubuntu[/noparse] hardy ...", for example.

---

### Post by Pandyrenim on 2008-08-20
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe deb-src 
[http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe deb 
[http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse deb-src 
[http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse deb

those are my line 50-55
i changed 53 to [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)
but it didn't help

---

### Post by todak on 2008-08-20
[http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe deb
[http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse deb-src
[http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse deb

should have deb in front of the http. Here is the corrected version:

```
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse 
deb http://security.ubuntu.com/ubuntu hardy-security multiverse 
```

---

### Post by pauper on 2008-08-20
Prepend "deb" to 53 and 55, and 54... try either "deb" or "deb-src".

[edit:]

Remove "deb" and "deb-src" at the end of any line.

---

### Post by Pandyrenim on 2008-08-20
That Did It, i feel kinda dumb, but Thanks for the help!

---

