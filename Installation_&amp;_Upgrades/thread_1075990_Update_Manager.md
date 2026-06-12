---
title: "Update Manager"
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by xtiano77 on 2009-02-20
I am trying to run the Update Manager application, but it stops when reading packet number 33 of 42 and it comes back telling me that it was unable to connect to the repositories.  Is this a problem with my system or are the repositories down temporarily?

---

### Post by taurus on 2009-02-20
Close down the update manager.  Then, open a terminal and run these two commands.

```
sudo apt-get update
sudo apt-get upgrade
```
Post the whole output if there is a problem with either command.

---

### Post by Perryg on 2009-02-20
> **xtiano77 said:**
> I am trying to run the Update Manager application, but it stops when reading packet number 33 of 42 and it comes back telling me that it was unable to connect to the repositories.  Is this a problem with my system or are the repositories down temporarily?

More than likely there is a problem either with the repository or latency or some other problem between you and them.  If you know you have Internet connectivity I would wait a bit and try again.

---

### Post by xtiano77 on 2009-02-20
I had access yesterday, but nothing today.  It might be a problem with the repository since I have been trying since around 5pm central time and still nothing.

---

### Post by betterhands on 2009-02-20
for me, sudo apt-get update freezes here: 

```
 Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out

```

---

### Post by xtiano77 on 2009-02-20
The Update Manager seems to be working now.

---

