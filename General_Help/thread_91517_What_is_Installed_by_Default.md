---
title: "What is Installed by Default"
date: 2005-11-17
forum: General Help
---

### Post by bobharp on 2005-11-17
I installed Breezy Badger awhile back and by fumbling around (and with the help of others) I have found that tools like 'gcc' and 'make' are not installed by default.  I was wondering if there was a list floating around of modules/programs installed on OS?

Thanks,
Bob

---

### Post by ranf on 2005-11-17
[QUOTE=bobharp]I installed Breezy Badger awhile back and by fumbling around (and with the help of others) I have found that tools like 'gcc' and 'make' are not installed by default.  I was wondering if there was a list floating around of modules/programs installed on OS?
[/QUOTE]
If you have a default install, type this (in a terminal):
```
dpkg --get-selections
```

Or look at the file on your installation CD:
/media/cdrom0/dists/breezy/main/binary-i386/Packages

I wonder why you ask this?

---

### Post by bobharp on 2005-11-17
ranf,

I'm having minor adjustment problems while getting familiar with Ubuntu.  I'm not a strong Linux user and Ubuntu has thrown me a few curves, as mentioned at the start of the thread.  Currently troubleshooting a connection refused while trying to open [http://localhost:9000](http://localhost:9000) .  This is my Slimserver ([www.slimdevices.com](www.slimdevices.com)) that I want to move from my Windows PC.  I am attempting to find out what is refusing the connection.  I do not believe a firewall is running.  I did get Samba working.

Thanks,
Bob

---

### Post by ranf on 2005-11-17
[QUOTE=bobharp]Currently troubleshooting a connection refused while trying to open [http://localhost:9000](http://localhost:9000) .[/QUOTE]
What is port 9000? And which software do you expect listening to this port?

---

### Post by bobharp on 2005-11-17
ranf,

It is the Slimserver.  I mentioned above.  Even when I try the url without the port ([http://localhost](http://localhost)) I get a connection refused error.

---

### Post by ranf on 2005-11-18
[QUOTE=bobharp]
It is the Slimserver.  I mentioned above.  Even when I try the url without the port ([http://localhost](http://localhost)) I get a connection refused error.[/QUOTE]
Without a port it would connect to port 80 by default. If you don't have Apache or any other http server running, then this is normal behaviour.

Please post the output of `ps ax'  (shows running programs)
and `sudo netstat -nultp' (shows which software listens to what port).

---

### Post by bobharp on 2005-11-18
ranf,

It seems that a restart fixed my issue.  Thanks for your help!

Bob

---

