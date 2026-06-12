---
title: "rapache synaptic package manager?"
date: 2009-03-19
forum: Installation &amp; Upgrades
---

### Post by berryboy on 2009-03-19
hello, i watched a tutorial and at the end showed rapache which looks real easy to use, in the tutorial he just used synaptic, but i did a search for it in synaptic and found nothing.. i have however downloaded rapache-0.07 but im unsure how to install this,
their website doesn't seem to have any instructions,any help would be great thank you

using sudo apt-get install rapache i get this
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package rapache

```

---

### Post by taurus on 2009-03-19
Which release are you running and have you enable all the repos, universe & multiverse, in System -> Administration -> Software Sources?

---

### Post by berryboy on 2009-03-19
thank you for your response.

i have just enabled universe & multiverse, also tried switching to a united kingdon server (from 'main server') still nothing here

Ubuntu 8.04.1 (desktop)

---

### Post by taurus on 2009-03-19
Looks like it is only available for intrepid, [http://packages.ubuntu.com/search?keywords=rapache&searchon=names&suite=intrepid&section=all](http://packages.ubuntu.com/search?keywords=rapache&searchon=names&suite=intrepid&section=all).

Now, where did you download the source file?  Did you download it from here?

[http://bazaar.launchpad.net/~rapache-devel/rapache/rapache-ubuntu/files/head%3A/rapache-0.7/](http://bazaar.launchpad.net/~rapache-devel/rapache/rapache-ubuntu/files/head%3A/rapache-0.7/)

---

