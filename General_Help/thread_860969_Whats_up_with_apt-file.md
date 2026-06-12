---
title: "Whats up with apt-file???"
date: 2008-07-16
forum: General Help
---

### Post by jimmy the saint on 2008-07-16
I just installed apt-file and when I ran the update, all that happens is that it says it cant get a whole lot of things.  The reason is that they don't exisit!!  all i get at those addresses are 404s.  Whats going on??  Here's the output

```
****@****:~$ sudo apt-file update
Can't get http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Contents-amd64.gz
Can't get http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Contents-amd64.gz
Can't get http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Contents-amd64.gz
Can't get http://archive.canonical.com/ubuntu/dists/hardy/Contents-amd64.gz
Can't get http://security.ubuntu.com/ubuntu/dists/hardy-security/Contents-amd64.gz
Can't get http://security.ubuntu.com/ubuntu/dists/hardy-security/Contents-amd64.gz
Can't get http://security.ubuntu.com/ubuntu/dists/hardy-security/Contents-amd64.gz
Can't get http://ppa.launchpad.net/gilir/ubuntu/dists/hardy/Contents-amd64.gz
Can't get http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/hardy/Contents-amd64.gz
```

Can I redirect apt-file to servers that contain these files??

Thanks 
JTS

---

### Post by Jim! on 2008-07-16
Do you have software sources enabled?

---

### Post by jimmy the saint on 2008-07-16
yeah.  The issue is that these files don'e exist on the servers. As I said, if you go there manually in a browser you just get 404 errors.

---

