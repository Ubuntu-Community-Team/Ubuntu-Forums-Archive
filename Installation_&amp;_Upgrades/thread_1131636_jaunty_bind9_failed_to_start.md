---
title: "jaunty bind9 failed to start"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by ciur.eugen on 2009-04-21
Hi everyone, 

I upgraded yesterday, Ubuntu 9.04 - Jaunty Jackalope from Interpid.  After
rebooting my PC, my Internet stopped to word. I checked around a little, and
found out that actually, network connectivity is fine (ping to a known IP
address gets a reply).  So... probably DNS problem. 

Indeed:
> sudo /etc/init.d/bind9 status
 * bind9 is not running
Then
> sudo /etc/init.d/bind9 start
 * Starting domain name service... bind9         [fail] 

>tail /var/log/daemon.log
Apr 21 08:03:30 eugen-laptop named[6134]: starting BIND 9.5.1-P2 -u bind -t /var/lib/named
Apr 21 08:03:30 eugen-laptop named[6134]: found 1 CPU, using 1 worker thread
Apr 21 08:03:30 eugen-laptop named[6134]: using up to 4096 sockets
Apr 21 08:03:30 eugen-laptop named[6134]: loading configuration from '/etc/bind/named.conf'
Apr 21 08:03:30 eugen-laptop named[6134]: none:0: open: /etc/bind/named.conf: permission denied
Apr 21 08:03:30 eugen-laptop named[6134]: loading configuration: permission denied
Apr 21 08:03:30 eugen-laptop named[6134]: exiting (due to fatal error)

The problem is that everything with that /etc/bind/named.conf seems fine,
because as you can see below there is full access to it.

>pwd
/var/lib/named/etc/bind

>ls -lsa
4 drwxr-sr-x 2 bind bind 4096 2009-04-21 01:59 .
4 drwxr-xr-x 3 root root 4096 2008-10-19 09:44 ..
4 -rwxrwxrwx 1 bind bind  237 2008-07-08 00:06 db.0
4 -rwxrwxrwx 1 bind bind  271 2008-07-08 00:06 db.127
4 -rwxrwxrwx 1 bind bind  237 2008-07-08 00:06 db.255
4 -rwxrwxrwx 1 bind bind  353 2008-07-08 00:06 db.empty
4 -rwxrwxrwx 1 bind bind  270 2008-07-08 00:06 db.local
4 -rwxrwxrwx 1 bind bind 2878 2008-07-08 00:06 db.root
4 -rwxrwxrwx 1 bind bind  907 2009-04-21 01:59 named.conf
4 -rwxrwxrwx 1 bind bind  165 2008-07-08 00:06 named.conf.local
4 -rwxrwxrwx 1 bind bind  572 2009-01-08 03:31 named.conf.options
4 -rwxrwxrwx 1 bind bind   77 2008-10-19 09:37 rndc.key
4 -rwxrwxrwx 1 bind bind 1317 2008-07-08 00:06 zones.rfc1918

Still - DNS is not resolving names... 
Smallest clue what the problem can be ? Is this a bug? Known issue?

---

### Post by ciur.eugen on 2009-04-21
Problem solved. It was because in old 8.10 I had disabled AppArmor, when installed 9.04 it enabled AppArmor again. There are some setting which I found in this forum how to solve that... however I make it simple - removed AppArmor again :)

---

### Post by korina on 2009-07-02
Well, I do have the same problem. I installed ubuntu 9.04 and after ISPconfig 2, everything was good and woorking well, and I decided to install  GUI (bad idea) and after reboot bind9 stopped working.
>tail /var/log/daemon.log
Jul  3 13:22:00 xiva named[4387]: none:0: open: /etc/bind/named.conf: permission denied
Jul  3 13:22:00 xiva named[4387]: loading configuration: permission denied
Jul  3 13:22:00 xiva named[4387]: exiting (due to fatal error)
Jul  3 13:22:13 xiva named[4426]: starting BIND 9.5.1-P2 -u bind -t /var/lib/named
Jul  3 13:22:13 xiva named[4426]: found 2 CPUs, using 2 worker threads
Jul  3 13:22:13 xiva named[4426]: using up to 4096 sockets
Jul  3 13:22:13 xiva named[4426]: loading configuration from '/etc/bind/named.conf'
Jul  3 13:22:13 xiva named[4426]: none:0: open: /etc/bind/named.conf: permission denied
Jul  3 13:22:13 xiva named[4426]: loading configuration: permission denied
Jul  3 13:22:13 xiva named[4426]: exiting (due to fatal error)
Any ideas about how to fix this fatal problem!

---

### Post by frodooooo39 on 2011-01-12
what should be the result of dig example.com if dns is working correctly. Here example.com is the domain name.

---

