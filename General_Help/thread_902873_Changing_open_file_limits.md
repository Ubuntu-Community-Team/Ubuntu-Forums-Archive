---
title: "Changing open file limits"
date: 2008-08-27
forum: General Help
---

### Post by shareme on 2008-08-27
Okay embarrassing question..

How do change the open file limits in Ubuntu?


From what I read in the login file I thought I would just put two entries in et/security/limits.conf and tit would be set higher..but no  still old 1024

Ubuntu Hardy Heron 8.0.4.1

And whoever has the correct answer first..Thank You..

---

### Post by pauper on 2008-08-28
Do _you_ know the correct answer?

Make sure that the following line in /etc/pam.d/login is uncommented:

```
session    required   pam_limits.so
```

An example:
```
:~$ grep -C 2 nofile /etc/security/limits.conf
#        - fsize - maximum filesize (KB)
#        - memlock - max locked-in-memory address space (KB)
#        - nofile - max number of open files
#        - rss - max resident set size (KB)
#        - stack - max stack size (KB)
--
#<domain>      <type>  <item>         <value>
#
john_doe         -       nofile          2048
#*               soft    core            0
#*               hard    rss             10000
```

Log out, log in. Run "ulimit -n" to see if changes took place.

Also see "man proc".

Search for **/**\/proc\/sys\/fs\/file-max string. The default value of
file-max is around 10% of RAM in KBs.

These commands should make proposed changes to fs/file-max and
fs/inode-max permanent (exclude angle brackets):

```
:~$ echo "
> fs.file-max = <new_value>
> fs.inode-max = <new_value>" | sudo tee -a /etc/sysctl.conf
:~$ sudo sysctl -p
```

---

### Post by shareme on 2008-09-02
No changes do take ulimit still shows 1024 open files limit

---

### Post by jigsaws on 2008-09-02
What about relogin or reboot?

---

### Post by shareme on 2008-09-02
Yes, doing reboot and relogin shows no change from 1024..

What I have done so far:

/etc/seurity/limits.conf

has 

root soft nofile 65000
*    soft nofile 65000


sysctl also has changes mentioned above..

---

### Post by fballem on 2008-09-02
> **shareme said:**
> Yes, doing reboot and relogin shows no change from 1024..

What I have done so far:

/etc/seurity/limits.conf

has 

root soft nofile 65000
*    soft nofile 65000


sysctl also has changes mentioned above..

I think you also need to set hard nofile limits as well, which should be at least the same number as in your sample.

By the way, if you want all users to have a 65000 open file limit, then there is no need to set a separate limit for root, since the * includes all users, including root.

Assuming that's what you want, may I suggest

* hard nofile 65000
* soft nofile 65000

You may want to pick a lower number (say multiples of 1024), since a number as high as 65000 will have a significant performance impact.

Hope this helps

---

### Post by shareme on 2008-09-02
no change ulimit still stats 1024 open files after I reboot.

Lets se I am only using Eclipse IDE nd runnign dev versions of j2ee app servers.  What happens if  I put

ulimit -n 4096 

in /etc/profile?  Would I get cannot change limit error or would that take for those logins that go through that?

---

### Post by shareme on 2008-09-02
There is a bug or set of bugs via PAM system..

I think I will have to set via all the profiles

---

