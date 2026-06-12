---
title: "Installing DNS Server (Bind9)"
date: 2009-08-23
forum: Installation &amp; Upgrades
---

### Post by p2bc on 2009-08-23
After a post I was trying to help out a couple of weeks ago, my interests were spired in setting up a DNS server (again).

Found an interesting guild on how to setup an over all server. Decided to actually implement the section on the DNS server on a virtual machine just to give it a go and well this is what ensued.

** Following code segments are from the guide **
```

apt-get install bind9

##For security reasons we want to run BIND chrooted so we have to do the
##following steps:
/etc/init.d/bind9 stop

##Edit the file /etc/default/bind9 so that the daemon will run as the unprivileged
##user bind, chrooted to /var/lib/named. Modify the line: OPTIONS="-u bind" so
##that it reads OPTIONS="-u bind -t /var/lib/named":
vi /etc/default/bind9

##Create the necessary directories under /var/lib:
mkdir -p /var/lib/named/etc
mkdir /var/lib/named/dev
mkdir -p /var/lib/named/var/cache/bind
mkdir -p /var/lib/named/var/run/bind/run

##Then move the config directory from /etc to /var/lib/named/etc:
mv /etc/bind /var/lib/named/etc

##Create a symlink to the new config directory from the old location (to avoid
##problems when bind gets updated in the future)
ln -s /var/lib/named/etc/bind /etc/bind

##Make null and random devices, and fix permissions of the directories:
mknod /var/lib/named/dev/null c 1 3
mknod /var/lib/named/dev/random c 1 8
chmod 666 /var/lib/named/dev/null /var/lib/named/dev/random
chown -R bind:bind /var/lib/named/var/*
chown -R bind:bind /var/lib/named/etc/bind

##Start up BIND, and check /var/log/syslog for errors:
/etc/init.d/bind9 start

```*PS: I love how they put that second to last line in, because there was an error.*

Ok, so everything went perfectly without a hitch until the last step with restarting.
Won't restart, I check the log and it says I don't have permission to do this action, although I am doing it as root. 

```

Aug 23 10:42:49 user-VM named[3116]: starting BIND 9.5.1-P2 -u bind -t /var/lib/na$
Aug 23 10:42:49 user-VM named[3116]: found 1 CPU, using 1 worker thread
Aug 23 10:42:49 user-VM named[3116]: using up to 4096 sockets
Aug 23 10:42:49 user-VM named[3116]: loading configuration from '/etc/bind/named.conf'
Aug 23 10:42:49 user-VM named[3116]: none:0: open: /etc/bind/named.conf: permission denied
Aug 23 10:42:49 user-VM named[3116]: loading configuration: permission denied
Aug 23 10:42:49 user-VM named[3116]: exiting (due to fatal error)

```
So I do a "ls -la /etc/bind/named.conf" and it says it belongs to "bind:bind".I go to the user and group management window to try a quick fix, I added myself and root to the "bind" group, nadda, no good still won't work. Tried "su bind" but seems there is a password  ???.

So my question, after all this, how do I get this bad boy working and what went wrong, or over looked. And is there a better way.

---

### Post by p2bc on 2009-08-25
No one has any suggestions???

---

### Post by jon64 on 2009-08-29
I'm in no way a linux guru but I have been working with bind9 as well. Have you tried to put the "bind" user in the "root" group just to see if that would work?

---

### Post by jon64 on 2009-08-29
I was searching Bind9 related problems in the ubuntuforums and i found this thread: [http://ubuntuforums.org/showthread.php?t=1131636&highlight=Bind9](http://ubuntuforums.org/showthread.php?t=1131636&highlight=Bind9) it seems like he had the same problem as you did and seems like he also used the same how-to as you did but he found a way to fix the problem. You may want to take a look at it and see if his methods will work for your situation as well.
 
Cheers! :popcorn::P

---

### Post by p2bc on 2009-08-29
Thx, I will check it out.

---

### Post by jon64 on 2009-08-30
Hey I was working with Bind9 prior to your post and was having problems with it as well but today I finally got things sorted out. Heres a link to my thread if you want to take a look at it. Maybe it'll help you setup your DNS server.

[http://ubuntuforums.org/showthread.php?p=7859761#post7859761](http://ubuntuforums.org/showthread.php?p=7859761#post7859761)

Cheers!:popcorn::P

---

### Post by p2bc on 2009-08-31
OK, for this problem as it is posted, the problem was resolved  by disabling/removing AppArmor application.

Thx for the help, I see I now I got to do a lot reading to figure out how to get everything working as it should.

Thx again.

---

### Post by JHan816 on 2009-09-14
Check out this thread:
 
[http://ubuntuforums.org/showthread.php?t=735188](http://ubuntuforums.org/showthread.php?t=735188)
 
There is a Bind9 profile setting for Apparmor. See the #9 post for a fix. This applies to Hardy but I think it may help here.
 
I hope this helps, I was about to install Bind9 and do this too. 
 
--John

---

### Post by p2bc on 2009-09-15
Thx, I will check it out.

---

### Post by JHan816 on 2009-09-19
I installed Bind9 and did not chroot it like the above instructions. I have it set up as a caching nameserver for now and it is working.
 
 I wonder if chrooting bind is still needed when it is running under Apparmor...

---

