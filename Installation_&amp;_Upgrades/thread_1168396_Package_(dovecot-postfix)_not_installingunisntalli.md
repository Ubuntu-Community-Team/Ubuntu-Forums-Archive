---
title: "Package (dovecot-postfix) not installing/unisntalling"
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by deekthesqueak on 2009-05-24
I'm working on my 9.04 server and for some reason dovecot-postfix will not install or uninstall properly.

```
sudo apt-get -V install dovecot-imapd
Reading package lists... Done
Building dependency tree
Reading state information... Done
dovecot-imapd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up dovecot-postfix (1:1.1.11-0ubuntu4) ...
dpkg: error processing dovecot-postfix (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 dovecot-postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I think it happened then I was moving around some files in /etc

Any suggestions on how to get it to properly uninstall so I can reinstall?

---

### Post by dabang on 2009-05-24
You could try -f option...
```
apt-get install -f <package>
```
or
```
apt-get purge <package>
```
to remove the package.
But maybe you can remember what you did to /etc and fix it?

---

### Post by deekthesqueak on 2009-05-24
I should have put more detail in the post but I was pretty tired last night. I have tried all manner of apt-get flags (-f, -V off the top of my head) and dpkg (--remove & --install).  I think what I did was after I removed it once I deleted /etc/dovecot to get rid of any config files and now it doesn't like it at all.
I've also tried apt-get --reinstall install dovecot-postfix and and apt-get purge dovecot-postfix and neither works.

---

### Post by deekthesqueak on 2009-05-24
Running sudo aptitude remove dovecot-postfix gets:
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
The following packages will be REMOVED:
  dovecot-postfix
0 packages upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 119kB will be freed.
Writing extended state information... Done
(Reading database ... 19149 files and directories currently installed.)
Removing dovecot-postfix ...
mv: cannot stat `/etc/dovecot/dovecot-postfix.conf': No such file or directory
dpkg: error processing dovecot-postfix (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 dovecot-postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
```
It looks like it is looking for /etc/dovecot/dovecot-postfix.conf and isn't there and errors out. Is there any way to fix this?

---

### Post by deekthesqueak on 2009-05-24
I fixed it.  What I ended up doing was getting the source and taking the dovecot-example.conf file and putting the contents of that into /etc/dovecot/dovecot-postfix.conf and they removing it with ```
apt-get remove dovecot-postfix
```

---

### Post by deekthesqueak on 2009-05-24
Well I have run into a new problem when installing dovecot-postfix here is the important part of the output.

```
Setting up dovecot-common (1:1.1.11-0ubuntu4) ...
Not replacing deleted config file /etc/dovecot/dovecot-ldap.conf
Not replacing deleted config file /etc/dovecot/dovecot-sql.conf
[: 72: /etc/ssl/certs/dovecot.pem: unexpected operator
Creating generic self-signed certificate:  /etc/ssl/certs/dovecot.pem ssl_key_file
```

My question is this, how do I get rid of any trace of dovecot-postfix and its associated programs dovecot-common dovecot-imapd dovecot-pop3d so I can get a fresh install of these programs going?

---

