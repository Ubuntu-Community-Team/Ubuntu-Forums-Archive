---
title: "Can't find radius sql example files"
date: 2009-10-16
forum: Installation &amp; Upgrades
---

### Post by abasel on 2009-10-16
Following: [https://help.ubuntu.com/community/WifiDocs/CoovaChilli]("https://help.ubuntu.com/community/WifiDocs/CoovaChilli")

I tried running the following,

zcat /usr/share/doc/freeradius/examples/mysql.sql.gz | mysql -u root -p radius

Only to find that the above mentioned files don't exist. Radius installed fine (apt-get install freeradius freeradius-mysql).

I am using Ubuntu Server 9.

Can someone tell me where I can get these files?

---

### Post by abasel on 2009-10-16
K... found a page ([http://www.ibr.cs.tu-bs.de/cgi-bin/dwww?type=file&location=/usr/share/doc/freeradius/examples/db_mysql.sql.gz]("http://www.ibr.cs.tu-bs.de/cgi-bin/dwww?type=file&location=/usr/share/doc/freeradius/examples/db_mysql.sql.gz"))

Hopefully this works.

---

### Post by abasel on 2009-10-16
aagh I saved this file and then tried the following:

```
cat mysql.sql | mysql -u root -p radius
```

But I get:

> ERROR 1067 (42000) at line 155: Invalid default value for 'id'

Which refers to the last entry in the file ie

```
CREATE TABLE nas (
  id int(10) DEFAULT '0' NOT NULL auto_increment,
  nasname varchar(128) NOT NULL,
  shortname varchar(32),
  type varchar(30) DEFAULT 'other',
  ports int(5),
  secret varchar(60) DEFAULT 'secret' NOT NULL,
  community varchar(50),
  description varchar(200) DEFAULT 'RADIUS Client',
  PRIMARY KEY (id),
  KEY nasname (nasname)
);
```


Any ideas

---

### Post by abasel on 2009-10-16
Think I worked it out... just documenting it for anyone else who did the same as me... 

Just worked out from the following:

> Note: for freeradius 2

That I am proably using freeradius 2 and there need to use 

```
mysql -u root -p radius < /etc/freeradius/sql/mysql/schema.sql
mysql -u root -p radius < /etc/freeradius/sql/mysql/nas.sql

```

Instead :-)

---

### Post by abean on 2009-11-18
Hey there,

I am also having trouble using freeradius2 and finding a work around for the file. Trouble is I don't have the mysql directory you spcified either... Any more details? Or could you send me the scripts?

Found it... 

#sudo apt-get install freeradius-mysql

Then the directories are there :)

---

### Post by abasel on 2009-11-18
Sorry but I only have what is in the link at the top of this thread.

---

