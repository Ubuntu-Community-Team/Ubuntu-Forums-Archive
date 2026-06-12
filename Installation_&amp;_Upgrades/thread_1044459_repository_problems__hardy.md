---
title: "repository problems  hardy"
date: 2009-01-19
forum: Installation &amp; Upgrades
---

### Post by phil2park2 on 2009-01-19
every time i try to  update  my  computer, i get this message when the  update installer reloads i get this message:
[SIZE="5"]
 GPG error: [http://deb.mulx.net](http://deb.mulx.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B1F5957DE4946268Failed to fetch [http://repoubuntusoftware.info/dists/harty/all/binary-amd64/Packages.gz](http://repoubuntusoftware.info/dists/harty/all/binary-amd64/Packages.gz)  302 Found
Some index files failed to download, they have been ignored, or old ones used instead.[/SIZE]

---

### Post by Pumalite on 2009-01-19
Edit your /etc/apt/sources.list and comment out the offending lines.
Post:
```
cat /etc/apt/sources.list
```

---

