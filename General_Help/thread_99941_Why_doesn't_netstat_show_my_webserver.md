---
title: "Why doesn't netstat show my webserver?"
date: 2005-12-06
forum: General Help
---

### Post by Kronocide on 2005-12-06
Hi,

netstat --inet -l

doesn't list my webserver even when it is up on port 80, as demonstrated with

telnet localhost 80
GET /

and

ps -ef | grep httpd.

netstat only lists hpiod, python, and cupsd.

Does anyone know what's going on?

---

### Post by moberry on 2005-12-06
Try netstat --all

---

### Post by Kronocide on 2005-12-06
Thanks for the tip, but even if that had worked it would not solve the mystery. It would have meant that netstat in Ubuntu doesn't consider httpd listening on port 80 an Internet server.

It doesn't work though, still doesn't show it. This was by the way the case for all my students at the course I'm giving, so chances are good it's the case on your 'puter as well. Is something broken?

---

### Post by moberry on 2005-12-06
netstat -l only shows connected sockets. Chances are your httpd is/was not connected to a host.

I think.. i could be wrong.

---

### Post by DrBair on 2005-12-06
Are you running netstat as root? You won't be able to see it as a lowly user.

---

### Post by Kronocide on 2005-12-06
Hold on, I found it. httpd is not listed in netstat as running tcp, but tcp6! That's not even explained in netstat's man page. Apparently that's why it doesn't consider httpd an Internet server, which of course is completely fubared... :-/

---

### Post by Kronocide on 2005-12-06
What the hell... There is nothing called "tcp6" in /etc/protocols but TCP has protocol *number* 6. Something looks broken...

---

### Post by Kronocide on 2005-12-06
This is an install from the standard Apache source distro. When I make the same install in Slackware it shows up in netstat in the normal way, so I guess this is an Ubuntu bug?

---

