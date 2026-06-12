---
title: "Ibex repository not updating"
date: 2008-10-26
forum: General Help
---

### Post by LonelyTraveler on 2008-10-26
Hi,

When I run apt-get update, this is what I get:
```

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.bz2  Hash Sum mismatch

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.bz2  Hash Sum mismatch

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.bz2  Hash Sum mismatch

W: Failed to fetch http://za.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.bz2  Hash Sum mismatch
```

I guess it is because of this that I can not install gstreamer. How do I fix this repository. I just installed Ibex.

Thanks.

---

### Post by LonelyTraveler on 2008-10-26
I just changed my repository from the South African one to the main one, and now I get this:

```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://archive.ubuntu.com intrepid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

```

---

### Post by LonelyTraveler on 2008-10-26
I got this sorted by going to the server option in the software sources and selecting other and then letting it choose the best server. Works perfectly after that.

---

### Post by cvmostert on 2009-01-06
I will try this thanks... hope it works...

---

