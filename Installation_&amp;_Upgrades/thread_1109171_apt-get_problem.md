---
title: "apt-get problem"
date: 2009-03-28
forum: Installation &amp; Upgrades
---

### Post by J-E-N-O-V-A on 2009-03-28
"E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"

I get this message in terminal, it's obvious that there is another package manager being used, however I don't know what it is! I've previously used the commands 'aptitude' and 'apt-get' but thought the processes had finished. 

Question: How can I find out what the conflicting process is and terminate it?

---

### Post by mikewhatever on 2009-03-28
Do you have Synaptic or Add/Remove open?

---

### Post by Chemical Imbalance on 2009-03-28
Also make sure that the automatic update icon is not active on your panel.

---

### Post by tommcd on 2009-03-28
Do you have the synaptic package manager or the Add / Remove package manager open when you are using apt-get? I have seen this when I forgot to close synaptic before using apt-get.

EDIT: Well, I guess we were all looking at this one. There were no replies when I started typing!

---

### Post by snova on 2009-03-28
dpkg, apt-get, aptitude, Synaptic, or Add/Remove, could all be causing it. But if you're certain you aren't running any of these, or something else, remove the lock file manually:

```
sudo rm /var/lib/dpkg/lock
```

---

