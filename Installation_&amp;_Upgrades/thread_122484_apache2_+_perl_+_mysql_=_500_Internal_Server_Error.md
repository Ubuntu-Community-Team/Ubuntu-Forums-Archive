---
title: "apache2 + perl + mysql = 500 Internal Server Error  ..."
date: 2006-01-27
forum: Installation &amp; Upgrades
---

### Post by browneyedgirl65 on 2006-01-27
I hope this is the right place...I searched on apache and on perl, but really nothing obvious (nor anyone describing the same problem).

Here's the poop: Trying to set up LAMP on my ubuntu installation for web development purposes (eg, "like" a server, but not an actual server). I'm using multiple user accounts, to duplicate the individual websites I'm developing and debugging before I upload them to their real sites.

So, I installed apache2 and configured it for cgi-bin, and it's running my plain perl scripts just fine.

I installed mysql and after a bit of hair pulling, I've been able to dump the copy of my production db into it, and the queries show the data is in there just fine. 

Now here's the problem: I don't seem to be able to run perl scripts that access the mysql database from the browser (500 internal server error).  But, I can run those same scripts on the command line, and they work.  The file is chmod 644 so I don't think it's a permissions thing.

I'm not quite sure what to make of this.  I'm especially stumped by being able to run the perl script in question on the command line and being able to run other perl scripts NOT trying to open mysql db's from the browser just fine.

Any replies welcome...

---

### Post by browneyedgirl65 on 2006-01-28
OK, just in case anyone runs into the same sort of thing, check if you 1) have an .htaccess file in that directory and 2) have not yet configured apache for htaccess.

Sheesh.

But, WOOT!  It works!

---

