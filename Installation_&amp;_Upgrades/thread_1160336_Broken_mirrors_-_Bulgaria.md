---
title: "Broken mirrors - Bulgaria"
date: 2009-05-15
forum: Installation &amp; Upgrades
---

### Post by cybershade on 2009-05-15
I live in Bulgaria and from about two days I can't download any packages from local repositories. Since I don't know who I have to contact, can you tell me what's going on? From 6 mirrors only two are working and the speed is very poor. I have 6 computers with Ubuntu and its critical to got access to them.

Here is the mirrors list:
mirrors.hitsol.net
ubuntu.hitsol.net
ubuntu.ipacct.com
ubuntu.linux-bg.com - Working
ubuntu.nano-box.net - Working

When I try to update the package list got this error:

W: Failed to fetch [http://repository.cairo-dock.org/ubuntu/dists/gutsy/cairo-dock/binary-i386/Packages](http://repository.cairo-dock.org/ubuntu/dists/gutsy/cairo-dock/binary-i386/Packages)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

Maybe the problem is in my computers, but after that apt doesn't work.

Any help is highly appreciated! Thanks! :)

---

### Post by zvacet on 2009-05-16
Just change server (to main maybe) and you should be O.K.I don´t know if you have local team in Bulgaria.If you do contact them.I tried your cairo-dock link and it doesn´t work.I think that is not something important so you can edit your source list and put # sign in front of that line and save and close file.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by cybershade on 2009-05-17
Thanks for your advice. Now the mirrors are working properly, so maybe something went wrong with the servers :)

---

