---
title: "Problems with new MySQL/phpMyadmin install"
date: 2008-12-03
forum: Installation &amp; Upgrades
---

### Post by vermax on 2008-12-03
Ok before I get started, I have googled, yahooed and everything in between before resorting to posting to solve this problem as it appears to be a problem that has been beaten to death but I simply can't solve it.  Warning:  I am very very new at this.

Ok I am runing the latest version of Ubuntu Server Edition.

I did apt-get install mysql-server and it installed 5.0 version

did apt-get install phpmyadmin and it installed phpmyadmin

I altered the apache2 config to include phpmyadmin and [http://myip.com/phpmyadmin](http://myip.com/phpmyadmin) comes up with the phpmyadmin login page like it should.

Now, when I try to login with username root and no password I get in but under create database it states No Privileges.

So then I try to do mysql -u root and I get the:

mysql> prompt.  No asking for a password or anything...

But anytime I try to make changes, such as add a username or change a password, or even add a password to root, it says access denied.

Any ideas?  Thanks in advance for any and all help.

Regards,

The n00b

---

