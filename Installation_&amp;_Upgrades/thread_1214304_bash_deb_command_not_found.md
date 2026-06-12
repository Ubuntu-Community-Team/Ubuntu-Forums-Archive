---
title: "bash: deb: command not found"
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by Wolvenreign on 2009-07-15
Hey everyone.

I'm trying to follow the install instructions for the Spring engine, but for some reason, my terminal does not recognize the "deb" command, as seen in...```
deb http://ppa.launchpad.net/spring/ppa/ubuntu jaunty main
```

Why is that? Is there any way to get the "deb" command recognized?

---

### Post by ibutho on 2009-07-15
You should add that line to the /etc/apt/sources.list file and then do
```
sudo apt-get update
sudo apt-get install spring
```

---

