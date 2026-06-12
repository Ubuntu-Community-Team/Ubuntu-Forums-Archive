---
title: "Access Oracle db on windows from ubuntu"
date: 2008-09-16
forum: General Help
---

### Post by twinkler_star on 2008-09-16
Linux n00b here.
I am trying to install Informatica on Ubuntu Hardy and it needs to access oracle db which is on windows machine (on same lan) to create repository.

I am not sure what I have to do to get this working.

Halp!

---

### Post by aloshbennett on 2008-09-17
Install an Oracle Client on your linux machine. This will create the necessary environment with tnsnames.ora and sqlplus etc..
Once you have an oracle home, verify you have set the following env variables set:
ORACLE_HOME
TNS_ADMIN
LD_LIBRARY_PATH

Add the entry for the db you want to access in your tnsnames.ora and that should be it.

---

