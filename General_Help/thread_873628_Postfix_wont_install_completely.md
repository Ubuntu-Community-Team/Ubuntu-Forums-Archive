---
title: "Postfix wont install completely"
date: 2008-07-29
forum: General Help
---

### Post by BlackDex on 2008-07-29
I Have a problem with installing postfix.
How can i fix this?

I get the following error:
```
$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up postfix (2.5.1-2ubuntu1) ...

Postfix configuration was not changed.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
postalias: fatal: open database /etc/aliases.db: Permission denied
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 1
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by BlackDex on 2008-07-29
bump

---

### Post by BlackDex on 2008-07-30
Hmm stil no help :(.
I realy want this to be fixed.

---

### Post by p_quarles on 2008-07-30
Well, it's indicating that /etc/aliases.db might be locked and somehow at the root of the problem. What is contained in that file?

---

### Post by BlackDex on 2008-07-31
Well... I don't have an aliases.db file.

```
$ ls -al aliases*
-rw-r--r--+ 1 root root 51 2008-07-24 11:59 aliases
```

---

### Post by sanocli on 2008-07-31
Hi,

Try to do :
```
sudo apt-get purge postfix
``` and then ```
sudo apt-get install postfix
```  

The first line will delete postfix with all its configuration files.

The second will install postfix.

I have always installed postfix like that and it works every time. I hope it will be the same for you.

---

### Post by BlackDex on 2008-08-01
I did that a few times already.
I did it again. Still same result.

---

### Post by BlackDex on 2008-08-04
Can some help me with this?
It is really frustrating.

---

### Post by brian_p on 2008-08-04
> **BlackDex said:**
> Can some help me with this?
It is really frustrating.

I don't use postfix but can use Google. Searching with '/etc/aliases.db' throws up some leads.

---

### Post by BlackDex on 2008-08-25
Well it was those ACL's.
When i removed it from the /etc/fstab file en rebooted.
It all worked.
But now all the files still have an + sign, and i can't get them away.

---

