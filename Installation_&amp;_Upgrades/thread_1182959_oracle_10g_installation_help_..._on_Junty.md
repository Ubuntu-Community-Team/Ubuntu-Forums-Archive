---
title: "oracle 10g installation help ... on Junty"
date: 2009-06-09
forum: Installation &amp; Upgrades
---

### Post by gaurang on 2009-06-09
hie all ,

i recently installed oracle 10g ( std. installation ) on ubuntu 9.04 ... with a little help from [this post]("http://blog.fekw.de/2008/06/10/oracle-database-10g-r2-on-kubuntu-804-32bit/")(i know its a bits older , but its still good for sure) and google ...

and after installation , i was able to open oracle EM web interface too and was able to look around in it ...

but after i restarted my laptop ... i'm now not able to open it ... i get "page can't be displayed" message ... 

i am sure that i am missing something very little ... but i'm still learning linux .. so i can't figure out the problem ... bt my guess is its because my laptop connects to router via wifi .. so may be its because of DHCP ... :( ... ( i know how to setup static ip using loopback adapter in windows but have no clue how to do that in linux )

any suggestion will be very helpful ...

thanks ...

---

### Post by oogie72 on 2009-10-22
Hi,

It could be because the Oracle Enterprise Manager (aka "dbconsole") was not started again. Try the following steps (assuming your database is up and running after the reboot) :

1) Set your ORACLE_SID variable to the correct database
2) Run the command "emctl status dbconsole" - that should report a url looking address and port # .

If it looks like it gave some sort of error or otherwise reporting it is not active, issue the command "emctl start dbconsole" - it too will spit back the url once up.

I'll come back in the morning with actual examples from my databases at work.

Cheers.

---

### Post by oogie72 on 2009-10-23
> **oogie72 said:**
> Hi,

It could be because the Oracle Enterprise Manager (aka "dbconsole") was not started again. Try the following steps (assuming your database is up and running after the reboot) :

1) Set your ORACLE_SID variable to the correct database
2) Run the command "emctl status dbconsole" - that should report a url looking address and port # .

If it looks like it gave some sort of error or otherwise reporting it is not active, issue the command "emctl start dbconsole" - it too will spit back the url once up.

I'll come back in the morning with actual examples from my databases at work.

Cheers.

As promised, the following is from one of my RHEL database servers. Hostname was purposely hidden for security reaseons, and I run the c-shell here at the office:
```

[FONT="Courier New"]$ setenv ORACLE_SID OOGIE
$ emctl status dbconsole
TZ set to Canada/Atlantic
Oracle Enterprise Manager 10g Database Control Release 10.2.0.4.0
Copyright (c) 1996, 2007 Oracle Corporation.  All rights reserved.
**http://<hostname_hidden>:1158/em**/console/aboutApplication
Oracle Enterprise Manager 10g is running.
------------------------------------------------------------------
Logs are generated in directory /mnt/hpdraid/oracle/product/10.2.0/<hostname_hidden>_OOGIE/sysman/log
[oracle7@lnxhpd ~]$[/FONT]
```

I purposely bolded a section of the url reported above - it is the section I keep bookmarked in my web browser. If you have more than one database instance on the system and are using invidual dbconsoles for each, Oracle usually uses a separate port to connect to each database's enterprise manager console. 

Finally, where the emctl command was mentioned above, the middle parameter is usually one of [FONT="Courier New"]status|start|stop[/FONT] (similar to other oracle components like lsnrctl). 

Hope that helps.

---

