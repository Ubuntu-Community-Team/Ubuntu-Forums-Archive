---
title: "What is restarting my machine?"
date: 2009-09-05
forum: Hardware
---

### Post by mattgyver83 on 2009-09-05
Im running Jinzora2, and Jinzora 3 (latest svn) on my 9.04 server.  All works fine externally when other users access the system.

However, internally it is very flakey.  If you are unfamiliar Jinzora is a CMS for music that uses Apache, PHP, and MySQL and lets you allow users to login to the system and download/stream/rate/request music shared on the serving computer.  

Here is the issue, when i login, at certain times and files if I click the link to play a song the entire server will physically restart as if someone hit the reset button.

This isnt quite random, this occurs on the same files, each time.  I have tested with multiple users accessing from the outside and they are able to run these files from the outside without a problem, but when I myself try inside, boom!  It is important to note that this site can be accessed 3 ways.
1) Port 80 redirect setup via no-ip.com
2) Host setup at no-ip.com host : port , which translates the address.
3) IP : port

All of these methods, internally with my LAN create this error.

Ive spent some time looking at logs, reproducing errors but cannot determine what is at fault here.  Im really looking for someone with a bit more advanced view to help point me in the right direction as I am completely lost. 

Not to bloat the post, please tell me what logs you wish to see, or errors you would like to see and I can post whatever is necessary.

Thanks in advanced!

[update]

I just want to note that further investigation of the logs I have ruled Apache out of the equation as the only error that is returned was a missing image during crash.  I am currently verifying that there are no PHP issues.

As I dont expect one to have the magic answer please comment with suggestions so that I may narrow this issue down.  Thanks.

---

### Post by mattgyver83 on 2009-09-06
bump.

I have reproduced a failure test and below are the *tail -f* for most relevant log files.  The Actual crash occurred at 15:33:02, you will note that only 1 log file shows any activity at, or around that time.  It is due to a missing image file within the theme that is set for Jinzora.

/var/log/apache2/error.log
----------------
```
matt@mamp:/var/log/apache2$ sudo tail -f error.log
[sudo] password for matt: 
[Sun Sep 06 15:04:39 2009] [error] [client 192.168.1.2] File does not exist: /var/www/favicon.ico
[Sun Sep 06 15:04:42 2009] [error] [client 192.168.1.2] File does not exist: /var/www/favicon.ico
[Sun Sep 06 15:04:42 2009] [error] [client 192.168.1.2] File does not exist: /var/www/favicon.ico
[Sun Sep 06 15:05:06 2009] [error] [client 192.168.1.2] File does not exist: /var/www/jinzora2/style/slick/add-fav.gif, referer: http://71.252.2.149:880/jinzora2/index.php?jz_path=CKY&ext.html
[Sun Sep 06 15:10:05 2009] [info] removed PID file /var/run/apache2.pid (pid=3045)
[Sun Sep 06 15:10:05 2009] [notice] caught SIGTERM, shutting down
[Sun Sep 06 15:11:59 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Sun Sep 06 15:11:59 2009] [info] Server built: Aug 18 2009 14:26:31
[Sun Sep 06 15:11:59 2009] [debug] prefork.c(1032): AcceptMutex: sysvsem (default: sysvsem)
[Sun Sep 06 15:20:49 2009] [error] [client 192.168.1.2] File does not exist: /var/www/jinzora2/style/slick/add-fav.gif, referer: http://71.252.2.149:880/jinzora2/index.php?jz_path=CKY&ext.html
[Sun Sep 06 15:33:26 2009] [error] [client 192.168.1.2] File does not exist: /var/www/jinzora2/style/slick/add-fav.gif, referer: http://71.252.2.149:880/jinzora2/index.php?jz_path=65daysofstatic&ext.html

```


/var/log/auth.log
-----------------
```
matt@mamp:/var/log$ sudo tail -f auth.log
[sudo] password for matt: 
Sep  6 15:26:33 mamp sshd[3616]: Accepted password for matt from 192.168.1.41 port 58059 ssh2
Sep  6 15:26:33 mamp sshd[3616]: pam_unix(sshd:session): session opened for user matt by (uid=0)
Sep  6 15:27:45 mamp sshd[3656]: Accepted password for matt from 192.168.1.41 port 58060 ssh2
Sep  6 15:27:45 mamp sshd[3656]: pam_unix(sshd:session): session opened for user matt by (uid=0)
Sep  6 15:28:37 mamp sshd[3693]: Accepted password for matt from 192.168.1.41 port 58063 ssh2
Sep  6 15:28:37 mamp sshd[3693]: pam_unix(sshd:session): session opened for user matt by (uid=0)
Sep  6 15:30:01 mamp CRON[3721]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep  6 15:30:04 mamp CRON[3721]: pam_unix(cron:session): session closed for user root
Sep  6 15:30:12 mamp sudo:     matt : TTY=pts/1 ; PWD=/var/log/apache2 ; USER=root ; COMMAND=/usr/bin/tail -f error.log
Sep  6 15:30:19 mamp sudo:     matt : TTY=pts/2 ; PWD=/var/log ; USER=root ; COMMAND=/usr/bin/tail -f auth.log
Sep  6 15:30:24 mamp sudo:     matt : TTY=pts/3 ; PWD=/var/log ; USER=root ; COMMAND=/usr/bin/tail -f dmesg
Sep  6 15:30:30 mamp sudo:     matt : TTY=pts/4 ; PWD=/var/log ; USER=root ; COMMAND=/usr/bin/tail -f kern.log
Sep  6 15:30:36 mamp sudo:     matt : TTY=pts/5 ; PWD=/var/log ; USER=root ; COMMAND=/usr/bin/tail -f mysql.err
Sep  6 15:31:01 mamp sudo:     matt : TTY=pts/6 ; PWD=/var/log/php5 ; USER=root ; COMMAND=/usr/bin/tail -f error.log
Sep  6 15:31:07 mamp sudo:     matt : TTY=pts/7 ; PWD=/var/log ; USER=root ; COMMAND=/usr/bin/tail -f syslog

```


/var/log/dmesg
--------------
```
matt@mamp:/var/log$ sudo tail -f dmesg
[sudo] password for matt: 
[   27.052375] type=1505 audit(1252264287.364:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1850
[   27.053644] type=1505 audit(1252264287.364:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1850
[   27.238462] type=1505 audit(1252264287.544:9): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=1854
[   27.372702] type=1505 audit(1252264287.684:10): operation="profile_load" name="/usr/sbin/slapd" name2="default" pid=1858
[   27.493570] type=1505 audit(1252264287.804:11): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1862
[   27.587730] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   37.730089] eth0: no IPv6 routers present
[   41.531778] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   41.531790] Bluetooth: BNEP filters: protocol multicast
[   41.631398] Bridge firewalling registered
```



/var/log/kern.log
-----------------
```
matt@mamp:/var/log$ sudo tail -f kern.log
[sudo] password for matt: 
Sep  6 15:11:30 mamp kernel: [   27.053644] type=1505 audit(1252264287.364:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1850
Sep  6 15:11:30 mamp kernel: [   27.238462] type=1505 audit(1252264287.544:9): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=1854
Sep  6 15:11:30 mamp kernel: [   27.372702] type=1505 audit(1252264287.684:10): operation="profile_load" name="/usr/sbin/slapd" name2="default" pid=1858
Sep  6 15:11:30 mamp kernel: [   27.493570] type=1505 audit(1252264287.804:11): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1862
Sep  6 15:11:30 mamp kernel: [   27.587730] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  6 15:11:37 mamp kernel: [   37.730089] eth0: no IPv6 routers present
Sep  6 15:11:41 mamp kernel: [   41.531778] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Sep  6 15:11:41 mamp kernel: [   41.531790] Bluetooth: BNEP filters: protocol multicast
Sep  6 15:11:41 mamp kernel: [   41.631398] Bridge firewalling registered
Sep  6 15:11:58 mamp kernel: [   58.214511] ip_tables: (C) 2000-2006 Netfilter Core Team
```



/var/log/php5/error.log
-----------------------
```
matt@mamp:/var/log/php5$ sudo tail -f error.log 
[sudo] password for matt: 
[06-Sep-2009 14:53:43] PHP Warning:  rsort() expects parameter 1 to be array, boolean given in /var/www/jinzora2/popup.php on line 2081
[06-Sep-2009 14:53:43] PHP Warning:  Invalid argument supplied for foreach() in /var/www/jinzora2/popup.php on line 2082

```


/var/log/syslog
---------------
```
matt@mamp:/var/log$ sudo tail -f syslog
[sudo] password for matt: 
Sep  6 15:11:43 mamp anacron[2952]: Anacron 2.3 started on 2009-09-06
Sep  6 15:11:44 mamp anacron[2952]: Normal exit (0 jobs run)
Sep  6 15:11:44 mamp /usr/sbin/cron[2999]: (CRON) INFO (pidfile fd = 3)
Sep  6 15:11:44 mamp /usr/sbin/cron[3000]: (CRON) STARTUP (fork ok)
Sep  6 15:11:44 mamp /usr/sbin/cron[3000]: (CRON) INFO (Running @reboot jobs)
Sep  6 15:11:58 mamp kernel: [   58.214511] ip_tables: (C) 2000-2006 Netfilter Core Team
Sep  6 15:17:01 mamp console-kit-daemon[2555]: WARNING: Couldn't read /proc/2554/environ: Failed to open file '/proc/2554/environ': No such file or directory 
Sep  6 15:17:01 mamp /USR/SBIN/CRON[3260]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep  6 15:20:02 mamp /USR/SBIN/CRON[3333]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep  6 15:30:01 mamp /USR/SBIN/CRON[3728]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
```

---

### Post by mattgyver83 on 2009-09-07
Okay,

I have opened the box, and now have determined that I have 11 bad capacitors inside this machine.  I have ordered replacements for these however could anyone verify that my symptoms match that of bad capacitors?

*Note the restarts are not random, they occur mainly when playing specific files within Jinzora, or trying to transfer files to the server via sftp*

.. yeah, this server is long gone, it blew the heck up.  darn capacitors ;)

---

