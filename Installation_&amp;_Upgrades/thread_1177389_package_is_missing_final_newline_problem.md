---
title: "package is missing final newline problem"
date: 2009-06-03
forum: Installation &amp; Upgrades
---

### Post by busstation16 on 2009-06-03
For the last week, I haven't been able to update because I keep getting an error that "'human-icon-theme' is missing final newline."

I have tried a lot of things I found online, and nothing seemed to work. But, i just went to:

/var/lib/dpkg/info

opened human-icon-theme.list with vi, went to the bottom and deleted everything that didn't look like a path (there was a bunch of random chars at the bottom.)

I don't know if this was a terrible idea, but it seems to have fixed my problem, and updates are running smoothly now.

---

### Post by Partyboi2 on 2009-06-04
Hi, open a terminal  and try
```
echo -en '\n' | sudo tee -a /var/lib/dpkg/info/human-icon-theme.list
```then
```
sudo apt-get update
sudo apt-get upgrade
```

---

