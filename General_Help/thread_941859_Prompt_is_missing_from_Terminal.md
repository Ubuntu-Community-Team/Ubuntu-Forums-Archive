---
title: "Prompt is missing from Terminal"
date: 2008-10-08
forum: General Help
---

### Post by revchris on 2008-10-08
I just installed Likewise Open and added the domain user to admin by typing in "sudo adduser DOMAIN\\name admin" and am logging onto the computer with DOMAIN\name.  Every time I start a terminal all I get is the blinking cursor and can't see anything I type.  If I expand the terminal window the prompt appears along with anything I've typed.
This does not happen when I'm logged in the local account.

Has anyone else experienced this with domain users?

---

### Post by Titan8990 on 2008-10-08
If I had to guess I would say that it is because when you create a local user it is assigned a default shell. Your domain users might not have got a default shell.

---

### Post by revchris on 2008-10-08
the default is set to /bin/bash

I changed it to /bin/sh and I just got a $ at the prompt and when I type in bash I go back to just having a cursor.  I would rather use bash than sh although it seems to be a bash issue.

Thanks

---

### Post by russlar on 2008-10-08
try tcsh.

---

