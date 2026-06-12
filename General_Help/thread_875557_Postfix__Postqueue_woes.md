---
title: "Postfix / Postqueue woes"
date: 2008-07-30
forum: General Help
---

### Post by protogenesis on 2008-07-30
Tried to set up a virtual host last night.  Failed miserably.  Since then, I've had some interesting issues with /var/log/mail.log  

When I type "mailq -v" I am getting this long list of what appears to configuration information:


[email]80730223002.A232835CFE@MY_HOSTNAME.org[/email]>
Jul 30 18:30:02 MY_HOSTNAME postfix/qmgr[22022]: A232835CFE: from=<root@MY_HOSTNAME.org>, size=614, nrcpt=1 (queue active)
Jul 30 18:30:02 MY_HOSTNAME postfix/local[22212]: A232835CFE: to=<MY_USERNAME@MY_HOSTNAME.org>, orig_to=<root>, relay=local, delay=0.13, delays=0.03/0.08/0/0.03, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Jul 30 18:30:02 MY_HOSTNAME postfix/qmgr[22022]: A232835CFE: removed
Jul 30 22:08:01 MY_HOSTNAME postfix/smtpd[22404]: connect from localhost[127.0.0.1]
Jul 30 22:08:19 MY_HOSTNAME postfix/smtpd[22404]: 8297E35CFD: client=localhost[127.0.0.1]
Jul 30 22:08:20 MY_HOSTNAME postfix/smtpd[22404]: disconnect from localhost[127.0.0.1]
Jul 30 22:09:46 MY_HOSTNAME dovecot: pop3-login: Disconnected: Inactivity: rip=###.###.###.###, lip=192.168.2.50, TLS handshake
Jul 30 22:12:37 MY_HOSTNAME dovecot: pop3-login: Login: user=<MY_USERNAME>, method=PLAIN, rip=###.###.###.###, lip=192.168.2.50, TLS
Jul 30 22:12:37 MY_HOSTNAME dovecot: POP3(MY_USERNAME): Disconnected: Logged out top=0/0, retr=0/0, del=0/0, size=0
Jul 30 22:17:29 MY_HOSTNAME dovecot: pop3-login: Login: user=<MY_USERNAME>, method=PLAIN, rip=###.###.###.###, lip=192.168.2.50, TLS
Jul 30 22:17:29 MY_HOSTNAME dovecot: POP3(MY_USERNAME): Disconnected: Logged out top=0/0, retr=0/0, del=0/0, size=0
Jul 30 22:19:42 MY_HOSTNAME dovecot: pop3-login: Login: user=<MY_USERNAME>, method=PLAIN, rip=###.###.###.###, lip=192.168.2.50, TLS
Jul 30 22:19:42 MY_HOSTNAME dovecot: POP3(MY_USERNAME): Disconnected: Logged out top=0/0, retr=0/0, del=0/0, size=0
Jul 30 22:19:50 MY_HOSTNAME dovecot: pop3-login: Disconnected: rip=###.###.###.###, lip=192.168.2.50, TLS handshake
Jul 30 23:41:58 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  mail
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  all
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: name_mask: all
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  MY_HOSTNAME.org
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  org
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  PostfixJul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  postfixJul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  postfixJul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  postdrop
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  MY_HOSTNAME.org, MY_HOSTNAME, localhost
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  /etc/mailname
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  /usr/lib/postfix
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  /var/lib/postfix
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  /usr/sbin
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  /var/spool/postfix
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  pid
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  all
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  double-bounce
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  nobody
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  hash:/etc/aliases
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  20080216
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  2.5.1
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  hash
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  deferred, defer
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  +
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: expand $mydestination -> MY_HOSTNAME.org, MY_HOSTNAME, localhost
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: expand $relay_domains -> MY_HOSTNAME.org, MY_HOSTNAME, localhost
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  TZ MAIL_CONFIG LANG
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  MAIL_CONFIG MAIL_DEBUG MAIL_LOGTAG TZ XAUTHORITY DISPLAY LANG=C
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  subnet
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  +=
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  -=+
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  debug_peer_list,fast_flush_domains,mynetworks,permit_mx_backup_networks,qmqpd_authorized_clients,relay_domains,smtpd_access_maps
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  bounce
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  cleanupJul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  defer
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  pickup
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  qmgr
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  rewriteJul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  showq
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  error
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  flush
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  verify
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  trace
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  100s
Jul 30 23:41:59 MY_HOSTNAME last message repeated 3 times
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  3600s
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  3600s
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  5s
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  5s
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  1000s
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  1000s
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  10s
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  10s
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  1s
Jul 30 23:41:59 MY_HOSTNAME last message repeated 3 times
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  500s
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  500s
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  18000s
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  18000s
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  1s
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  1s
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  192.168.0.0/24, 127.0.0.0/8
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: inet_addr_local: configured 2 IPv4 addresses
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: inet_addr_local: configured 2 IPv6 addresses
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  static:anyone
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: dict_eval: const  static:anyone
Jul 30 23:41:59 MY_HOSTNAME postfix/postqueue[22656]: connect to subsystem public/showq
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  mail
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  all
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: name_mask: all
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  MY_HOSTNAME.org
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  org
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  PostfixJul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  postfixJul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  postfixJul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  postdrop
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  MY_HOSTNAME.org, MY_HOSTNAME, localhost
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  /etc/mailname
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  /usr/lib/postfix
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  /var/lib/postfix
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  /usr/sbin
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  /var/spool/postfix
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  pid
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  all
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  double-bounce
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  nobody
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  hash:/etc/aliases
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  20080216
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  2.5.1
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  hash
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  deferred, defer
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  +
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: expand $mydestination -> MY_HOSTNAME.org, MY_HOSTNAME, localhost
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: expand $relay_domains -> MY_HOSTNAME.org, MY_HOSTNAME, localhost
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  TZ MAIL_CONFIG LANG
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  MAIL_CONFIG MAIL_DEBUG MAIL_LOGTAG TZ XAUTHORITY DISPLAY LANG=C
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  subnet
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  +=
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  -=+
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  debug_peer_list,fast_flush_domains,mynetworks,permit_mx_backup_networks,qmqpd_authorized_clients,relay_domains,smtpd_access_maps
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  bounce
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  cleanupJul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  defer
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  pickup
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  qmgr
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  rewriteJul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  showq
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  error
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  flush
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  verify
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  trace
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  100s
Jul 30 23:42:02 MY_HOSTNAME last message repeated 3 times
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  3600s
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  3600s
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  5s
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  5s
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  1000s
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  1000s
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  10s
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  10s
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  1s
Jul 30 23:42:02 MY_HOSTNAME last message repeated 3 times
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  500s
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  500s
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  18000s
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  18000s
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  1s
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  1s
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  192.168.0.0/24, 127.0.0.0/8
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: inet_addr_local: configured 2 IPv4 addresses
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: inet_addr_local: configured 2 IPv6 addresses
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  static:anyone
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: dict_eval: const  static:anyone
Jul 30 23:42:02 MY_HOSTNAME postfix/postqueue[22658]: connect to subsystem public/showq
MY_HOSTNAME:~#


I thought I fixed this earlier when I flushed the cache on my machine - heard this was related to an out of memory/memory running low error.  Now, it's back.  I cannot figure out from where it is generated, how to fix it or the like.  I have no mail in the queue, btw.

Any thoughts???

---

