---
title: "installing proftp on 8.04"
date: 2009-01-19
forum: Installation &amp; Upgrades
---

### Post by Alf Stockton on 2009-01-19
I am following the howto at [http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p6](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p6)
to get proftp working at my server but I get the following messages when I attempt to start proftp:-


/etc/init.d/proftpd start
 * Stopping ftp server proftpd                                          [ OK ]
 * Starting ftp server proftpd                                                  - notice: unable to bind to Unix domain socket at '/var/run/proftpd/test.sock': Address already in use
 - notice: unable to listen to local socket: Operation not permitted
 - warning: the DisplayFirstChdir directive is deprecated and will be removed in a future release.  Please use the DisplayChdir directive.
localhost.localdomain - PRIVS_ROOT: unable to seteuid(): Operation not permitted
localhost.localdomain - PRIVS_ROOT: unable to setegid(): Operation not permitted 

......snip......

Suggestions please.

---

