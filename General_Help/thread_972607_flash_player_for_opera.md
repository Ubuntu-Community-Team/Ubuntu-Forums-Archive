---
title: "flash player for opera"
date: 2008-11-05
forum: General Help
---

### Post by rwarwarwa on 2008-11-05
HI there,

I don't seem to have a flashplayer installed for opera. The video doesn't show up in youtube.

How is it installed?

thank you.

rwa

---

### Post by zvacet on 2008-11-06
Opera use same flash player as Firefox.In **Opera>tools>preferences>advanced>content>plugin options>see if the path for flash is usr/lib/mozzila/plugins.**That is a path if you have new flash plugin inastalled(not flashplugin-nonfree).New fkash can be instaled from synaptic if you have this line in your source list

```
deb http://archive.canonical.com/ubuntu hardy partner
```

Change hardy to interpid if you run Interpid(obviously).Save file and close.

```
sudo apt-get update && sudo apt-get upgrade
```

---

