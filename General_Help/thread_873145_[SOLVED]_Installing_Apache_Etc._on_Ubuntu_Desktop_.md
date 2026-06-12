---
title: "[SOLVED] Installing Apache Etc. on Ubuntu Desktop (for development)"
date: 2008-07-28
forum: General Help
---

### Post by Jesdisciple on 2008-07-28
I have XAMPP for Linux but was recently advised that an updatable collection of packages from Apt would be a better idea, but I want to make sure, as best as I can, that I don't screw anything up.  Should I do anything before saving my web directory and uninstalling XAMPP?  And what packages should I get other than the obvious ones (Apache, MySQL, PHP)?

Thanks a bunch!

---

### Post by RealPSL on 2008-07-28
Complete guide [https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP]("https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP")

---

### Post by Jesdisciple on 2008-07-28
Before you posted, I decided to try on my own and installed a few packages.  After the below, I removed them but still get the same result.

I executed the following command as per the guide and entered my password twice...```
$ sudo tasksel install lamp-server
tasksel: aptitude failed (100)
```

What'd I do wrong?

---

### Post by Jesdisciple on 2008-07-29
Well, I found this...  [http://ubuntuforums.org/showthread.php?t=603326](http://ubuntuforums.org/showthread.php?t=603326)

I uninstalled as per the above guide and tried again, no dice.  So apparently my premature attempt wasn't the problem...

Help!

---

### Post by RealPSL on 2008-07-29
You are not the only one having this problem. Maybe the workaround in the second link can help you.
[URL="https://bugs.launchpad.net/ubuntu/+source/tasksel/+bug/131134"]
https://bugs.launchpad.net/ubuntu/+source/tasksel/+bug/131134 [/URL]
[http://ubuntuforums.org/showthread.php?t=514551]("http://ubuntuforums.org/showthread.php?t=514551")

---

### Post by Jesdisciple on 2008-08-08
RealPSL, I appreciate the links, but I didn't get anywhere with that either.  However, I [installed KDE]("http://ubuntuforums.org/showthread.php?t=876801") and [found that XAMPP no longer worked]("http://ubuntuforums.org/showthread.php?t=881392").  Come to find out, [KDE somehow fixed this problem]("http://www.apachefriends.org/f/viewtopic.php?p=123815").

Now, what can I do about this?  (I want to set my new web dir to my old one.)```
$ apache2 -d /home/chris/www
apache2: bad user name ${APACHE_RUN_USER}
$ echo ${APACHE_RUN_USER}

$ sudo apache2 -d /home/chris/www
[sudo] password for chris: 
apache2: bad user name ${APACHE_RUN_USER}
$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
```

EDIT:  I found [http://ubuntuforums.org/showthread.php?p=5456941]("http://ubuntuforums.org/showthread.php?p=5456941"), but wouldn't the cleaner solution be to get the /etc/apache2/envvars file recognized?

---

### Post by RealPSL on 2008-08-17
The error you are getting there is likely because there is only a short name in your /etc/hosts file > 127.0.1.1       my-desktop

If you changed it to be something like > 127.0.1.1       my-desktop my-desktop.example.com that error message should disappear.

Now the other error. Does www-data own the files in your target directory or have read access to them?

---

### Post by Jesdisciple on 2008-08-18
I'm sorry...  I should have marked this thread as solved and linked it to the solution.  I need to learn to keep my questions packaged neatly.  :)

But thank you for alerting me that the thread fell through the cracks.  The solution is at [http://ubuntuforums.org/showthread.php?t=886070]("http://ubuntuforums.org/showthread.php?t=886070").

---

