---
title: "failing to fetch Update servers"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by Shadowman13 on 2009-08-12
I keep having the same problem, whenever i got to update, or upgrade i keep getting the stupid lines like

> W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/Release](http://archive.ubuntu.com/ubuntu/dists/dapper/Release)  Unable to find expected entry  deb/binary-amd64/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.


i use the wget command, but is there anyway i can simply fix it? please help me out, i cant download anything thanks to this thing, Im really new to Ubuntu and dont know much about computers, so please when you explain... slow it down so i can keep up lol.

---

### Post by zvacet on 2009-08-12
In terminal 

> sudo apt-get update && sudo apt-get upgrade

Maybe you want to upgrade to next LTS Hardy Heron.If you do read [this.]("https://help.ubuntu.com/community/HardyUpgrades")

---

