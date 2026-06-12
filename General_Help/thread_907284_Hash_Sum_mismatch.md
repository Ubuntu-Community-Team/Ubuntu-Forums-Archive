---
title: "Hash Sum mismatch"
date: 2008-09-01
forum: General Help
---

### Post by _mrv on 2008-09-01
Hi all,

Any ideas what is causing these errors on my newly installed machine when trying to install new sw (nvidia driver via envy) ?

```

Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libx/libx11/libx11-dev_1.1.3-1ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libx/libx11/libx11-dev_1.1.3-1ubuntu2_i386.deb)  Hash Sum mismatch

```

This has nothing to do with envy though; I keep getting those errors from other packages as well (via synaptic).

EDIT: I'm still getting these from random packages; any ideas what's going on?

 -mrv-

---

### Post by _mrv on 2008-09-02
bump

---

### Post by _mrv on 2008-09-02
Just couple of minutes ago I tried to 'apt-get update' with Synaptic and got these errors:

Failed to fetch [http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/hardy/main/binary-i386/Packages.bz2](http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/hardy/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/hardy/universe/source/Sources.bz2](http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/hardy/universe/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Some index files failed to download, they have been ignored, or old ones used instead.

I'm getting mostly same errors even if I change the repository I'm using. Is this server-side issue or do I have something wrong in my Ubuntu installation (clean 8.04 install) ?

---

