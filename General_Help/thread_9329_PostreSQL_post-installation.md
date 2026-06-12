---
title: "PostreSQL post-installation"
date: 2004-12-27
forum: General Help
---

### Post by amerigo5 on 2004-12-27
After installing PostgreSQL using Synaptic, what should I do to start using PostgreSQL? Do I need to create the user 'postgres' first? Or it is already created during the installatioin? If so, what's the password? Anyway, I just need some pointers on how to start using PostgreSQL right after fresh install on Ubuntu. 

Thanks.

---

### Post by Juergen on 2004-12-28
The user postgres should exist, with a disabled password like root.

You should probably start by reading the docs in /usr/share/doc/postgresql-doc/html ;-)

To create a database-user (and his 'home'-db) try:
$ sudo su - postgres -c 'createuser yourlogin'
$ createdb yourlogin
Answer the two questions from createuser with 'y', so you'll have basic admin-rights. 

If that fails with a message like 'Can't connect to server' you probably have to look at the authentication methods. 
I just installed 'identd' but you may have security-concerns with this - then you have to configure one of the other methods.

If all works you should be able to connect to your 'home'-database with just running 'psql'.
Or maybe install pgaccess, if you want a gui.

---

### Post by amerigo5 on 2004-12-28
Got it to work. I didn't realize that I need 'sudo' infront of 'su postgres'. Thanks!

---

