---
title: "gForge package broken ?"
date: 2005-11-29
forum: General Help
---

### Post by santo on 2005-11-29
Someone who got gForge successfully installed on Breezy ?
I cannot get it installed :( 

first it couldn't find the startup script for postgress, but after creating a symlink, this was solved.
Next, it cannot start the postgress db:
> 
TCP/IP connections must be enabled for SSL


Ok, I disabled ssl for now (ssl = false in postgresql.conf) to get around this error.

Now, it's complaining about not finding
> 
/etc/postgresql/pg_hba.conf


apparently, postgres gets installed in /etc/postgresql/7.4/main and not in /etc/postgresql

When I rename /etc/postgresql to /etc/postgresql.org and then create a symlink /etc/postgresql which points to /etc/postgresql.org/7.4/main,
I can get passed this error too, but then postgres cannot create the required user, because it expects its files to be in /etc/postgresql/7.4/main

Any ideas/suggestions ?

---

