---
title: "Jaunty: Update manager loads and loads and loads..."
date: 2009-05-17
forum: Installation &amp; Upgrades
---

### Post by mickpf on 2009-05-17
Hi folks,

few weeks ago I installed jaunty-amd64 on my new notebook. It worked fine until I installed an unidentified update or a software package. I don't know which one. Since that the update manager loads a couple of MB's (about 600 MB !!!) every time I press the button "Check", which runs about an hour. Before that install it ran few seconds.

I've already cleaned the cache and executed 'apt-get update' but without any effect to this behavior.

Can any one help?

Kind Regards,
Michael

---

### Post by Kevbert on 2009-05-17
What do you get with the following commands in terminal
```
sudo apt-get clean
sudo apt-get autoclean
sudo apt get install -f 
```

---

### Post by mickpf on 2009-05-18
Hi Kevbert,

sorry, but your advice is without any effect...

I'm using ubuntu-9.04 (i386) in a vmware box and keeping actual also, but without this suspect behaviour of the update manager.
I believe, it is caused by a difference between i386 und amd64 binaries.

---

