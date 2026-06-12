---
title: "Update issue"
date: 2009-08-17
forum: Installation &amp; Upgrades
---

### Post by joe557 on 2009-08-17
[SIZE=4]Hello All, 

if any one can tell me why i am getting this error when i am updating my system?

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://bh.archive.ubuntu.com](http://bh.archive.ubuntu.com) jaunty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release](http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release)  

W: Failed to fetch [http://bh.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release](http://bh.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.


it have been more that 20 days which i am trying to fix this issue but still nothing at all.

if anyone can help me that would be great because the system is giving me an update error.

thanks, 
Joe

[/SIZE]

---

### Post by zvacet on 2009-08-17
In applications>accessories>terminal run 

```
sudo apt-get update && sudo apt-get upgrade
```

If that doesn´t help **system>admin>software sources **and change server.

---

### Post by solipsist on 2009-08-18
I think this is the standard error on all ubuntu systems.
I've tried different servers as well but nothing seems to work.
I get this msg almost everyday but i've started to ignore it; the system does work well though, without any issues.

---

