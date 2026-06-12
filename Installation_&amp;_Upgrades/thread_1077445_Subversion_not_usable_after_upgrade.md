---
title: "Subversion not usable after upgrade?"
date: 2009-02-22
forum: Installation &amp; Upgrades
---

### Post by DaleEMoore on 2009-02-22
Hi All;

I seldom commit to my subversion projects so I only recently noticed that I get the following error.

```
root@LakeNap:/srv/svn/repositories# svn info svn://localhost/svntest
svn: Can't connect to host 'localhost': Connection refused
```

I do not know if this is because xinetd is not running svnserve since 

```
dalem@LakeNap:~$ netstat -anp | less -I
```

does not show 3690 anywhere.

I've looked for xinetd, security or subversion errors in /var/log/messages and other log files and can find no trace of what is refusing the connection.

How do I diagnose what is complaining?

Many thanks for any help you can provide,
Dale E. Moore

---

### Post by DaleEMoore on 2009-02-24
Any suggestions you have are very much appreciated!

---

### Post by avtolle on 2009-02-24
Dale, take a look at /etc/host (or hosts) file and see if there is anything amiss there.

---

### Post by DaleEMoore on 2009-02-26
Thanks for the idea! Here is my /etc/hosts:

```
dalem@LakeNap:~$ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       LakeNap.moore.works.mw  LakeNap

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

It seems OK to me,
Dale E. Moore

---

### Post by DaleEMoore on 2009-02-27
I wonder how I can tell what's failing?

---

### Post by DaleEMoore on 2009-03-01
Any help or thoughts are appreciated!

(Please throw me a bone.)

---

### Post by DaleEMoore on 2009-03-06
Would someone please tell me where I should go to ask questions about diagnosing xinetd?

Many thanks for any thoughts you have,
Dale E. Moore

---

### Post by DaleEMoore on 2009-03-06
I learned how to log xinetd activity and implemented it.```
vi /etc/xinetd.conf
log_type = SYSLOG daemon info
/etc/init.d/xinetd restart
```
But that did not have the desired effect. There is nothing in ```
less /var/log/messages
```
and I have a new error.
```
svn list svn://localhost/svntest
Authentication realm: <svn://localhost:3690> d0e76d56-bffc-0310-aa7f-8e5018241ac9
Password for 'root': 
Authentication realm: <svn://localhost:3690> d0e76d56-bffc-0310-aa7f-8e5018241ac9
Username: dalem   
Password for 'dalem': 
```
Many thanks for any thoughts you have,
Dale E. Moore

---

