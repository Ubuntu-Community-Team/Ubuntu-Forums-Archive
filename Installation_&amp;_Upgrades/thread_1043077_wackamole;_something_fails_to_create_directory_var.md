---
title: "wackamole; something fails to create directory /var/run/wackamole"
date: 2009-01-18
forum: Installation &amp; Upgrades
---

### Post by mattbennett on 2009-01-18
Hello all,

I'm trying to run wackamole on 8.04 server edition. Using the default install from the repositories, the /etc/init.d/wackamole script fails to start the daemon.

The problem seems to be that the directory /var/run/wackamole does not exist, and something along the line fails to create it when writing the pid and socket file which are configured to live in it.

The installation procedure creates /var/run/wackamole, so everything seems to work initially, but of course after a restart /var/run gets wiped. At that point, manaully creating /var/run/wackamole will enable everything to work correctly again.

I have tried modifying /etc/init.d/wackamole to put the .pid file directly into /var/run, but it always seems to show up in /var/run/wackamole (or it fails to start if the dir doesn't exist), which suggests to me that it's the wackamole executable that's chosing where to write it.

I will try to recompile the binary to write the .pid to /var/run, but this is the repo version so everything should "just work". 

I'll report back with my findings, but if anyone has any insight into why it's broken I'd appreciate it.

Many thanks,
Matt.

P.S. I originally had this problem back on Edgy, and there's a half-finished thread to wackamole-users tackling the problem here: [http://www.gossamer-threads.com/lists/backhand/wackamole/2017?do=post_view_threaded#2017](http://www.gossamer-threads.com/lists/backhand/wackamole/2017?do=post_view_threaded#2017)

---

### Post by mattbennett on 2009-01-18
Although wackamole can be recompiled with the --with-pid-dir=PATH configure option, it's much easier to just modify the init script to check for the existence of /var/run/wackamole and create it if it's not there.

I've opened a bug report [1] with a patch that does exactly that.

Thanks for listening!

Matt.

[1] [https://bugs.launchpad.net/ubuntu/+source/wackamole/+bug/318459](https://bugs.launchpad.net/ubuntu/+source/wackamole/+bug/318459)

---

