---
title: "apt-get update timeout"
date: 2006-02-03
forum: Installation &amp; Upgrades
---

### Post by kharyett on 2006-02-03
For the last couple of days, I have been getting a timeout when doing an apt-get update.

Could not connect to ca.archive.ubuntu.com connection timeout.

Any problems that I should know about with that archive?

---

### Post by interse on 2006-02-03
Can't help, but I have a similar problem.  See my recent thread in Desktop Support under Synaptic Error Message.

---

### Post by kharyett on 2006-02-03
Fixed it.

I edited the /etc/apt/souces.list and removed every occurence of ca.archives.ubuntu.com and left them as archive.ubuntu.com.

No errors, works fine now.

---

