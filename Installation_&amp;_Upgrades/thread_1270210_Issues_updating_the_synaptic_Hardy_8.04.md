---
title: "Issues updating the synaptic Hardy 8.04"
date: 2009-09-19
forum: Installation &amp; Upgrades
---

### Post by aetherguy881 on 2009-09-19
I've had this problem for a while and am now wanting to do some thing about it.

Every time I try to update the synaptic package manager I keep getting the same error message:

```
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/source/Sources.gz  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/source/Sources.gz  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/source/Sources.gz  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/source/Sources.gz  404 Not Found [IP: 91.189.88.40 80]
Some index files failed to download, they have been ignored, or old ones used instead.
```

I don't know why it's trying to fetch from gusty... That makes no sense to me. I'm assuming this is left over from when I upgraded from gusty to hardy.

Any help will be greatly appreciated.

Thanks.

---

### Post by snowpine on 2009-09-19
```
gksu gedit /etc/apt/sources.list
```

And comment out (by typing # at the beginning of the line) or delete any lines that reference gutsy.

---

### Post by mithun.kamath on 2009-09-19
Hey aetherguy881,

Try this 
Go to System > Administration > Software Sources
Change Download From to main server

Just a few minute back i had the same issue and got solved with the help of WOJOX,

[http://ubuntuforums.org/showthread.php?t=1267690](http://ubuntuforums.org/showthread.php?t=1267690)

Regards,
Mithun

---

### Post by aetherguy881 on 2009-09-20
Ok, both methods have seemed to have worked.

Thanks!

---

