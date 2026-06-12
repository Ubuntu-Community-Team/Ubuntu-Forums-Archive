---
title: "[SOLVED] I have no proxy"
date: 2008-10-27
forum: General Help
---

### Post by notsomeone on 2008-10-27
IS THERE A WAY TO MARK THIS REOLVED?
(All I had to do was take the http_proxy out of .bashrc... and then reboot the system. Reboots always fix everything.)


I've been playing around with a web server on my PC for a while now, but I've just started moving the server files to another old PC. I installed LAMP and a few other services, and I can even load web pages from it, that is until I copied over my .profile and apache2.conf and a few other things.
I don't know which file screwed everything up, but now I cannot get apt-get updates, or php-pear updates or anything, because they all want to connect through a proxy (127.0.0.1:8118) which does not exist and I do not know where this setting is, aside from being able to change the address in .bashrc.
I tried just pointing them at privoxy on my computer 192.168.2.15:8118, but the connection is refused (not blocked by firewall, just refused).

---

### Post by dcstar on 2008-10-28
> **notsomeone said:**
> IS THERE A WAY TO MARK THIS REOLVED?
........

Use the THREAD TOOLS.

---

