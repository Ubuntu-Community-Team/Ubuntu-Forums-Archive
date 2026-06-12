---
title: "Installing cacti on ubuntu 8.04"
date: 2008-11-14
forum: General Help
---

### Post by markeee on 2008-11-14
Hi,

I followed the guide at [http://ubuntuforums.org/showthread.php?p=4446832](http://ubuntuforums.org/showthread.php?p=4446832)

For installing cacti, and everything went fine until it came to the graphs, none are being created

I hve tried installing from apt, and the same problem

rrdtool/snmp are both installed and i cannot see any problems,


anyone have any ideas?

---

### Post by mk6032 on 2009-06-28
I'm using a fresh install of 9.04. The graphs on my installation are not being created either. I ran into a few threads on the Cacti forum which suggested to run

```

sudo dpkg-reconfigure php5-mysql

```

But this doesn't return anything. I also ran
```

sudo dpkg-reconfigure debconf

```

and changed the level to low in order to see anything, and then re-ran the dpkg-reconfigure php5-mysql.... still no questions or anything returned.

Another forum suggested to manually run poller.php

```

sudo php /usr/share/cacti/site/poller.php > /home/<username>/poller.log

```

This returns some errors:

```

Warning: require(/etc/cacti/debian.php): failed to open stream: Permission denied in /usr/share/cacti/site/include/config.php on line 27

Fatal error: require(): Failed opening required '/etc/cacti/debian.php' (include_path='.:/usr/share/php:/usr/share/pear') in /usr/share/cacti/site/include/co
nfig.php on line 27

```

Like 27 of config.php says...

```

require('/etc/cacti/debian.php');

```

Check to see if /etc/cacti/debian.php exists:
```

$ ls -laF /etc/cacti/debian.php
-rw-r----- 1 root www-data 582 2009-06-27 21:30 /etc/cacti/debian.php
$

```

The problem lies within the permissions of this file. To fix..
```

sudo chown www-data:www-data /etc/cacti/debian.php
sudo chmod 755 /etc/cacti/debian.php

```

Re-run the poller to check that everything is ok..
```

sudo php /usr/share/cacti/site/poller.php > /home/<username>/poller.log
more /home/<username>/poller.log

```

You should now see lots of lines starting with OK. I can get this far... but still no dang graphs! Any suggestions?

---

