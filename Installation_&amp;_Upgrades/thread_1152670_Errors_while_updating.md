---
title: "Errors while updating"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by positron98 on 2009-05-08
Hello,

I get the following errors as I execute $sudo apt-get update

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

What's causing this?

Also, earlier, I removed Openoffice3.0 using Synaptic in order to upgrade to 3.1. I might have accidently removed some dependencies. How would I check if all dependencies are there and should I execute the following command to get them back?:

sudo apt-get install -f

Thank you for your help.

---

### Post by zvacet on 2009-05-08
> is another process using it?

Is add/remove or synaptic run in same time?If yes then turn them off and work just with CLI.Try to change server under system>admin>sortware sources.Maybe that way you will get updates.It doesn´t hurt to run 

```
sudo apt-get -f install
```

---

### Post by _Purple_ on 2009-05-08
Close your Synaptic Package Manager and then try to run
```
sudo apt-get update
```

---

### Post by positron98 on 2009-05-08
Thank you guys for your help!

---

