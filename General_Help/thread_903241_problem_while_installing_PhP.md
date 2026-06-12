---
title: "problem while installin\g PhP"
date: 2008-08-28
forum: General Help
---

### Post by vivek shekar on 2008-08-28
HI,

I have ubuntu8.04 LTS in my machine.
I have installed apache2 successfully.
Now i am trying to install PHP after restarting apache2 its giving following error mess....

root@vivek-desktop:~# /etc/init.d/apache2 restart
* Restarting web server apache2 apache2: apr_sockaddr_info_get() failed for vivek-desktop
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
httpd (no pid file) not running
apache2: apr_sockaddr_info_get() failed for vivek-desktop
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
(9Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

---

### Post by overdrank on 2008-08-28
Moved :)

---

### Post by rouben on 2008-09-01
Looks like when you restarted Apache before that, it didn't really shut down all that well. Then when apache tried to start up again and take over port 80, it obviously failed, because an older Apache instance was already using port 80 (which is the port that web servers use). The other errors about determining the server's fully qualified name can be ignored, unless you actually want to run a publically accessible web server on this computer. If you just want to play around with PHP scripts, don't worry about these errors.

A restart of your computer will definitely fix things, or you can try **sudo pkill -9 apache2** followed by **sudo /etc/init.d/apache restart**. The first command will kill off any rogue Apache instances that sneaked past your previous restart attempt, and I believe you know what the second command does already. :)

---

### Post by vivek shekar on 2008-09-27
LoadPlugin: failed to initialize shared library /usr/lib/firefox/plugins/nsdejavu.so [/usr/lib/firefox/plugins/nsdejavu.so: undefined symbol: XtShellStrings]

---

