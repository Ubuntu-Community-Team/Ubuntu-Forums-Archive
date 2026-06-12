---
title: "Cannot get packages for java6-jdk"
date: 2008-11-14
forum: General Help
---

### Post by keabuntu on 2008-11-14
Running sudo apt-get install sun-java6-jdk results in:
Couldn't find package sun-java6-jdk

Tried updating my sources.list to include universe, did not solve.

Any suggestions appreciated, this is for and Eclipse w/ PDT install.

I'm on HH.

---

### Post by Yellow Pasque on 2008-11-14
That package is in the multiverse

---

### Post by keabuntu on 2008-11-14
OK, just that simple.  Thank you, got it now, obviously newbie.

---

### Post by taurus on 2008-11-14
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```
Otherwise, go into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and put a check mark in front of all the repos except the last one, Source Code.  Press the Reload button and see if you can find **java** in the Search field.

---

