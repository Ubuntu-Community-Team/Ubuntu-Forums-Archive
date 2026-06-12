---
title: "unable to lock"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by rhoward on 2009-04-27
I am trying to install some upgrades and here is the message I am getting.  

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
 I am trying to remove/var/lib/dpkg/lock,because I think that is the source of my problem, but it seems no matter what I try from terminal I cannot remove it. I can't just delete it, it won't let me, I must remove it but how do I do that?
Some help please!!!
Thank you,
R Howard

---

### Post by Partyboi2 on 2009-04-27
Hi, before trying to remove the lock file you should make sure that you have no other package managers opened eg synaptic, apt-get, update-manager, dpkg. If none of those are open then open a terminal and type
```
ps -e
``` this will give a list of running processes check down the list that no package manager is running (synaptic, apt-get, update-manager, dpkg) if there is then you will need to kill the process which you can do with
```
sudo killall name
``` (replace name with name of process)
if there are no package manager processess running then remove the lock with
```
sudo rm /var/lib/dpkg/lock
```

---

