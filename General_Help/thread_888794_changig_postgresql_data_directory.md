---
title: "changig postgresql data directory"
date: 2008-08-13
forum: General Help
---

### Post by alenis on 2008-08-13
I installed postgres and I want to change the data directory to another location on a NAS device. I created the new directory, created a password for the postgres user, gave him the ownership of the new directory, changed the data_directory parameter in 

```
/etc/postgresql/8.3/mainpostgresql.conf
```

this way:

```
data_directory = '/media/nas/database/postgresql'
```

Then I tried to start postgres with the command 

```
/usr/lib/postgresql/8.3/bin/pg_ctl start -D /etc/postgresql/8.3/main/
```

getting the following message:

```
/media/nas/database$ 2008-08-13 17:21:55 GMT FATAL:  data directory "/media/nas/database/postgresql" has group or world access
2008-08-13 17:21:55 GMT DETAIL:  Permissions should be u=rwx (0700).
```

I changed the permission on the directory with the command:

```
sudo chmod 700 /media/nas/database/postgresql

```

which changed the permissions as expected

```
drwx------ 2 postgres postgres 0 2008-08-13 17:20 postgresql

```

the I issued again the command to start postgres getting exactly the same message as before. Susprisingly, the permissions on the directory where again:

```
drwxrwxrwx 2 postgres postgres 0 2008-08-13 17:20 postgresql

```


So, I really don't understand what's happening. Can anybody help?

---

