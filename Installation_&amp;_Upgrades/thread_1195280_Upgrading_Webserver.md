---
title: "Upgrading Webserver"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by ActivEcks on 2009-06-23
Ok, Im trying to upgrade ubuntu server. However, I can't lose alot of configuration. Its a webserver with about 30 websites and SQL database on it.

I've tried doing the upgrade but, that totally defuncted my machine. Lucky enough, Diskology makes a nice Hardware based cloner, and lucky enough, Im paranoid. So I have a duplicate drive that is identical.

Now, I don't think the upgrade is going to work. Is it (question) possible to do a new install, and move the config files and database and files over to the new machine.. and it kick off? Soft of hoping all the config files are stored locally, and not much it could be simple as duplicating IP info, and copying 5-10 folders across. Apache2, mysql, webmin... thats about it.

Any suggestions?

---

### Post by pytheas22 on 2009-06-23
In principle it should work to just reinstall Ubuntu, then copy in all of the files that are specific to your situation.  You would probably need to sort out some permissions issues after doing that, but it wouldn't be that bad.

To estimate how much work would be involved in rebuilding the server like this, however, it would help if you provided more information.  For example, how are the websites stored?  Does each site have a directory in /home/*/public_html?  How is the machine partitioned?  If you have /home on a dedicated partition, that would make things easier.

---

### Post by ActivEcks on 2009-06-23
The websites are stored in 
/home/www/domain.com/
/home/www/domain2.com/

Its one partition, 160gb hard drive. The partitions are:

120gb linux
5gb extended (5gb linux-swap inside extended)

I dont know enough about MySQL to be able t begin to understand where and what, same for webmin partially.

---

### Post by pytheas22 on 2009-06-23
If the websites are just in two directories, they shouldn't be hard to move over.

webmin may not actually require you to move any new files over at all, but I'm not sure.  You can backup /etc/webmin just in case.

I'm not an expert on MySQL, but I believe all the configuration files are in /etc/mysql, while the databases themselves are in /var/lib/mysql.

In principle, you should only need to copy over the stuff mentioned above, as well as /etc/apache2 and /etc/network/interfaces, and things should work.

If you have an extra machine available, or just a virtual machine, I'd go ahead and try setting this up to see how it works there before rebuilding the real server.

---

### Post by ActivEcks on 2009-06-23
Well, what I meant to mean was, the websites are in /home/www directory. There are about 30 directories in there. in individual folders. For example only:

/home/www/google.com/
/home/www/ubuntuforums.org/
/home/www/slashdot.org/

each site has a folder like that.

---

### Post by pytheas22 on 2009-06-24
> Well, what I meant to mean was, the websites are in /home/www directory. There are about 30 directories in there. in individual folders.

You should still be able to work with that.  Just copy over /home/www/*, adjust permissions as necessary, make sure Apache knows where the website files are, and it should be alright.

---

