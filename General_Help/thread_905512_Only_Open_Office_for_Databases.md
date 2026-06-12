---
title: "Only Open Office for Databases?"
date: 2008-08-30
forum: General Help
---

### Post by K.Morgan on 2008-08-30
I was wondering if there are any other database software available for Ubuntu apart from what Open Office has to offer.

I going to be needing Database software to manage a load of stock for my business soon and was wondering what the options were.

---

### Post by EmanresuusernamE on 2008-08-30
Could you be a bit more specific?  As in you need something like access, or you need an actual engine for databases?  MySQL is a database engine and many companies use it, or do you need a program to access the data in the database such as MS Access?

---

### Post by gnuwatch on 2008-08-30
MYSQL is great and is used by the industry.

---

### Post by mb_webguy on 2008-08-30
Well, if you want a *real* database, you can get MySQL...  As far as creating the database structure, MySQL Administrator is pretty easy to work with assuming you know the basic concepts of relational databases.  For entering data and performing queries, MySQL Query Browser is fairly decent, but you have to know how to put together an SQL statement.  I'm sure there are some user-friendly, drag-and-drop front-ends for MySQL somewhere...

EDIT: Grrr...  I'm always the last to get a post in.  Next time I'm just going to post one word, just to be sure I'm first.  Maybe "The"...

---

### Post by Nepherte on 2008-08-30
MySQL, PostgreSQL or Oracle.

---

### Post by K.Morgan on 2008-08-30
Thanks.  I've never used databases before so don't really know where to start, so looking at all available options.  I need something quite simple that just enables me to gain quick access to items so i know what i have in stock at all times.

Doesn't need to be fancy or that powerful just something to keep track.

Will check out suggestions made.

---

### Post by EmanresuusernamE on 2008-08-30
Do you need multiple users to access the database at one time, or will it just be one system accessing the data?

---

### Post by K.Morgan on 2008-08-30
It will be just one system accessing.

---

### Post by Nepherte on 2008-08-30
MySQL is pretty easy to use in combination with phpMyAdmin. It's a web based front end to create/edit tables and records in MySQL and much more. It requires you to setup a local web server though (which is not hard). This is a good place to start: [https://help.ubuntu.com/community/phpMyAdmin](https://help.ubuntu.com/community/phpMyAdmin)

---

### Post by EmanresuusernamE on 2008-08-30
> **K.Morgan said:**
> It will be just one system accessing.
Personally, I don't recommend using any external SQL engines then.  However this will limit your ability for this to grow in the future at the same time.

---

### Post by K.Morgan on 2008-08-30
Thanks for your help, got lots of things to look at and learn.

---

