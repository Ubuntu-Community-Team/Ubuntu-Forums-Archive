---
title: "postgres doesn't work after ibex upgrade"
date: 2009-02-28
forum: Installation &amp; Upgrades
---

### Post by BryanKeith on 2009-02-28
Hello, I can't seem to get the postgres 8.2 server to start after upgrading to Intrepid Ibex.  /etc/init.d/postgresql-8.3 works as expected, but /etc/init.d/postgresql-8.2 doesn't reply.

```
$ /etc/init.d/postgresql-8.2 start
$ /etc/init.d/postgresql-8.3 start
 * Starting PostgreSQL 8.3 database server                
                  [ OK ]
$ /etc/init.d/postgresql-8.3 stop
 * Stopping PostgreSQL 8.3 database server                                    
                  [ OK ]
$ /etc/init.d/postgresql-8.2 stop
$
```

I don't think I used to have 8.3 installed.  Was it installed during the upgrade?

I can get psql to connect to the 8.3 server but not the 8.2 server, but I think that's because 8.2 isn't running.  How can I tell if it's running?

Bryan

---

### Post by BryanKeith on 2009-03-02
I'm not sure if it was the OS upgrade or the application upgrade that I did immediately after, but postgres 8.2 was uninstalled and postgres 8.3 was installed.  This meant that I didn't have any access to my databases on 8.2.  Since 8.2 isn't included in the intrepid repositories, I put the hardy repositories back into /etc/apt/sources.list and then was able to reinstall postgres 8.2.  It went something like this:

```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.intrepid
sudo cp /etc/apt/sources.list.distUpgrade /etc/apt/sources.list
sudo apt-get upgrade
sudo apt-get install postgresql-8.2
sudo cp /etc/apt/sources.list.intrepid /etc/apt/sources.list
```

I'm sure there are more specific lines to simply add to sources.list, but this is what worked for me.

Bryan

---

