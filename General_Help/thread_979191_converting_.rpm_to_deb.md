---
title: "converting .rpm to deb"
date: 2008-11-11
forum: General Help
---

### Post by c0da on 2008-11-11
Hi,

I want to convert e2fsprogs-devel.rpm to e2fsprogs-devel.deb. I use alien but got the following error.

```

sudo alien -d e2fsprogs-devel-1.40.8-2.fc9.i386.rpm

```


```

warning: e2fsprogs-devel-1.40.8-2.fc9.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: e2fsprogs-devel-1.40.8-2.fc9.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: e2fsprogs-devel-1.40.8-2.fc9.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: e2fsprogs-devel-1.40.8-2.fc9.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: e2fsprogs-devel-1.40.8-2.fc9.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: e2fsprogs-devel-1.40.8-2.fc9.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: e2fsprogs-devel-1.40.8-2.fc9.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: e2fsprogs-devel-1.40.8-2.fc9.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: e2fsprogs-devel-1.40.8-2.fc9.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: e2fsprogs-devel-1.40.8-2.fc9.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: e2fsprogs-devel-1.40.8-2.fc9.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: e2fsprogs-devel-1.40.8-2.fc9.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: e2fsprogs-devel-1.40.8-2.fc9.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: e2fsprogs-devel-1.40.8-2.fc9.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: e2fsprogs-devel-1.40.8-2.fc9.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: e2fsprogs-devel-1.40.8-2.fc9.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
Warning: Skipping conversion of scripts in package e2fsprogs-devel: postinst postrm
Warning: Use the --scripts parameter to include the scripts.
warning: e2fsprogs-devel-1.40.8-2.fc9.i386.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
e2fsprogs-devel_1.40.8-3_i386.deb generated

```

The .deb file is corrupted and of course unusable. What am I doing wrong?

---

