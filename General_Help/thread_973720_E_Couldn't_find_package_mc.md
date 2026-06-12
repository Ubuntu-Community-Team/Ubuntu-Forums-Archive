---
title: "E: Couldn't find package mc"
date: 2008-11-06
forum: General Help
---

### Post by gotix on 2008-11-06
Sorry for naive question, but I can't install midnight commander.

I uncomented the lines in /etc/apt/sources.list:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid universe
...
for universe and for multiverse.

a search on the ubuntu web page says midnight commander package exists:
[http://packages.ubuntu.com/search?keywords=mc&searchon=names&suite=intrepid&section=all](http://packages.ubuntu.com/search?keywords=mc&searchon=names&suite=intrepid&section=all)

but if try "apt-get install mc", I get:
"E: Couldn't find package mc"
also,  "aptitude search mc"
finds 23 packages (mce-dev, mono-gmcs), but mc is not in the list

---

### Post by zvacet on 2008-11-07
```
sudo apt-get update && sudo apt-get upgrade
```

In synaptic search box type **mc** and when you find it install it.

---

### Post by gotix on 2008-11-07
sorry I was not able to test that, it was a fresh 8.10 install, and when I rebooted, Ubuntu refused to start. So I installed an 8.04, and there it works without problems
Anyways I will remember "apt-get update", that is a very good thing to know.

---

### Post by zvacet on 2008-11-07
Everytime afer you add new repo to the your source list you have to run 

```
sudo apt-get update
```

to refresh your source list.

---

