---
title: "Postgres permissions problem"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by mateusz.fiolka on 2009-10-09
Hi,

I'm having a problem with permissions on Postgres in Ubuntu. My procedure looks like this:

sudo apt-get install postgresql
sudo /etc/init.d/postgresql stop

// change /etc/postgresql/8.3/main/pg_hba.conf
// local all all password

sudo /etc/init.d/postgresql start

// now I should be able to use pgsql using user passwords

sudo su postgresql
psql

CREATE DATABASE testdb;
CREATE USER testuser;
\password testuser; # assigning password
GRANT ALL ON testdb TO testuser;

// now I disconnect and connect as the user
psql -U testuser -d testdb

// successfully connected, BUT:
// cannot add any table nor even do a select on any table
// every time I get permission error

Anyone knows what may be the problem? Am I doing something wrong? Or maybe I'm missing something?

Thanks,
Matt

---

