---
title: "Cacti Issues"
date: 2008-11-05
forum: General Help
---

### Post by sgardne on 2008-11-05
Hi all,

I am trying to get Cacti working on my Ubuntu 7.10 server. I originally installed it and had it working somewhat, but not to satisfaction, so I uninstalled everything, and used dpkg --purge to get rid of everything instead of just manually deleting everything, and this seemed to help as I was asked all the initial questions during the install. However, I got a strange notice:
> WARNING: include path for php has changed!

libphp-adodb is no longer installed in /usr/share/adodb. New installation path is now /usr/share/php/adodb.

Please update your php.ini file. Maybe you must also change your web-server configuration.
I am not entirely sure what this means. When I run the poller manually now I get this output on the command line:
> sh: -: not found
11/05/2008 02:04:05 PM - POLLER: Poller[0] Maximum runtime of 292 seconds exceeded. Exiting.
11/05/2008 02:04:05 PM - SYSTEM STATS: Time:292.9695 Method:cmd.php Processes:1 Threads:N/A Hosts:2 HostsPerProcess:2 DataSources:0 RRDsProcessed:0

Warning: pclose(): 48 is not a valid stream resource in /usr/share/cacti/site/lib/rrd.php on line 47
I also get this message when i point firefox at the cacti page:
> Fatal error: Call to undefined function mysql_pconnect() in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 376
I would really love to get this working. If anyone can clue me in to what I'm doing wrong, I would be forever grateful.

This is [cross-posted in the cacti]("http://forums.cacti.net/viewtopic.php?t=29735&start=0&postdays=0&postorder=asc&highlight=") user forums. There is a bit more information about my initial process there, but I think I've got all the relevant detail here.

---

