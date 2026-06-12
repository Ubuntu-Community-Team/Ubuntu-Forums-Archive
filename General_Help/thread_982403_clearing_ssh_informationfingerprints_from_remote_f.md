---
title: "clearing ssh information/fingerprints from remote file management"
date: 2008-11-14
forum: General Help
---

### Post by thefatmoop on 2008-11-14
when ubuntu logs into ssh server for the first time it stores the rsa fingerprint. 

and if these need to be cleared for terminal logins it's easy..but How do i remove the rsa fingerprints from menu: places > connect to server > ssh

i reformatted a server and updated everything and now its using the old iinfo... now i cant connect to it to edit files

---

### Post by Steve1961 on 2008-11-14
You need to remove the old signature from ~/.ssh/known_hosts.  Just edit the file and delete the old fingerprint.

---

