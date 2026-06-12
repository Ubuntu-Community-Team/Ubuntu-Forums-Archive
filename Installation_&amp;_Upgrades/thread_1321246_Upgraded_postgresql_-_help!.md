---
title: "Upgraded postgresql - help!"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by optimus2861 on 2009-11-09
I just upgraded from 9.04 to 9.10, which in the process "upgraded" postgresql from 8.3 to 8.4. I put quotes on the word upgraded because I can't seem to get anything functional on either version now. I was only using postgresql as the amarok 1.4 database backend; I'd like to either get 8.3 running again or upgrade that database to 8.4. 

I found a short list of instructions on upgrading an 8.3 database to 8.4, but it depends on getting 8.3 to run. I try to start it and nothing happens:

```
root@merrithewi-desktop:init.d# pg_ctlcluster 8.3 main start
Error: pg_controldata not found, please install postgresql-8.3

```I admit I glossed over the postgre message the system spit at me during the upgrade, not really understanding it, and assuming the upgrade would leave things in a working state.

Anyone got some pointers?

---

### Post by jarofgreen on 2009-11-10
I have no data I want to keep, so I just removed and reinstalled the packages.

You may have to edit /etc/postgresql/8.4/main/postgresql.conf to say ```
port = 5432
```

Hopefully someone will post better instructions!

---

### Post by optimus2861 on 2009-11-10
No, the 8.4 postgresql configuration is already set to port 5432, and it will run just fine. I just can't get 8.3 to run; it's set for port 5433, FYI, presumably so they can run side by side. If 8.3 would run that is.

---

### Post by ewanchic on 2009-11-10
I had the same problem this morning. What happened is Karmic DID uninstal 8.3, but left your etc files ("nice";))

just: sudo apt-get install postgresql-8.3
and then: /etc/init.d/postgresql-8.3 start

Then you'll see the [OK]. From there, it sounds like you know what to do as far as moving the DBs over to 8.4

---

### Post by optimus2861 on 2009-11-11
Yup, that was it. I seem to be up & running with 8.4 now.

---

