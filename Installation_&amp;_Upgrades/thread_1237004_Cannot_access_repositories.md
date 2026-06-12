---
title: "Cannot access repositories"
date: 2009-08-10
forum: Installation &amp; Upgrades
---

### Post by cmat on 2009-08-10
I haven't been able to access the repositories for almost a week. I don't know what I did to cause this. Internet works fine and Ubuntu on my other PC work great. I already changed the server in software settings to main and get the same results. Please help, I can't install any software or updates. 

```
sudo apt-get update
Ign http://archive.ubuntu.com jaunty Release.gpg
Ign http://archive.ubuntu.com jaunty/universe Translation-en_CA
Ign http://archive.ubuntu.com jaunty/restricted Translation-en_CA
Ign http://archive.ubuntu.com jaunty/multiverse Translation-en_CA
Ign http://archive.ubuntu.com jaunty/main Translation-en_CA
Ign http://archive.ubuntu.com jaunty-updates Release.gpg
Ign http://archive.ubuntu.com jaunty-updates/universe Translation-en_CA
Ign http://archive.ubuntu.com jaunty-updates/restricted Translation-en_CA
Ign http://archive.ubuntu.com jaunty-updates/multiverse Translation-en_CA
Ign http://archive.ubuntu.com jaunty-updates/main Translation-en_CA
Ign http://archive.ubuntu.com jaunty-security Release.gpg
Ign http://archive.ubuntu.com jaunty-security/universe Translation-en_CA
Ign http://archive.ubuntu.com jaunty-security/restricted Translation-en_CA
Ign http://archive.ubuntu.com jaunty-security/multiverse Translation-en_CA
Ign http://archive.ubuntu.com jaunty-security/main Translation-en_CA
Ign http://archive.ubuntu.com jaunty-backports Release.gpg
Ign http://archive.ubuntu.com jaunty-backports/universe Translation-en_CA
Ign http://archive.ubuntu.com jaunty-backports/multiverse Translation-en_CA
Ign http://archive.ubuntu.com jaunty-backports/restricted Translation-en_CA
Ign http://archive.ubuntu.com jaunty-backports/main Translation-en_CA
Ign http://archive.ubuntu.com jaunty Release
Ign http://archive.ubuntu.com jaunty-updates Release
Ign http://archive.ubuntu.com jaunty-security Release
Ign http://archive.ubuntu.com jaunty-backports Release
Ign http://archive.ubuntu.com jaunty/universe Packages
Ign http://archive.ubuntu.com jaunty/restricted Packages
Ign http://archive.ubuntu.com jaunty/multiverse Packages
Ign http://archive.ubuntu.com jaunty/main Packages
Ign http://archive.ubuntu.com jaunty-updates/universe Packages
Ign http://archive.ubuntu.com jaunty-updates/restricted Packages
Ign http://archive.ubuntu.com jaunty-updates/multiverse Packages
Ign http://archive.ubuntu.com jaunty-updates/main Packages
Ign http://archive.ubuntu.com jaunty-security/universe Packages
Ign http://archive.ubuntu.com jaunty-security/restricted Packages
Ign http://archive.ubuntu.com jaunty-security/multiverse Packages
Ign http://archive.ubuntu.com jaunty-security/main Packages
Ign http://archive.ubuntu.com jaunty-backports/universe Packages
Ign http://archive.ubuntu.com jaunty-backports/multiverse Packages
Ign http://archive.ubuntu.com jaunty-backports/restricted Packages
Ign http://archive.ubuntu.com jaunty-backports/main Packages
Ign http://archive.ubuntu.com jaunty/universe Packages
Ign http://archive.ubuntu.com jaunty/restricted Packages
Ign http://archive.ubuntu.com jaunty/multiverse Packages
Ign http://archive.ubuntu.com jaunty/main Packages
Ign http://archive.ubuntu.com jaunty-updates/universe Packages
Ign http://archive.ubuntu.com jaunty-updates/restricted Packages
Ign http://archive.ubuntu.com jaunty-updates/multiverse Packages
Ign http://archive.ubuntu.com jaunty-updates/main Packages
Ign http://archive.ubuntu.com jaunty-security/universe Packages
Ign http://archive.ubuntu.com jaunty-security/restricted Packages
Ign http://archive.ubuntu.com jaunty-security/multiverse Packages
Ign http://archive.ubuntu.com jaunty-security/main Packages
Ign http://archive.ubuntu.com jaunty-backports/universe Packages
Ign http://archive.ubuntu.com jaunty-backports/multiverse Packages
Ign http://archive.ubuntu.com jaunty-backports/restricted Packages
Ign http://archive.ubuntu.com jaunty-backports/main Packages
Err http://archive.ubuntu.com jaunty/universe Packages
  404 Not Found
Err http://archive.ubuntu.com jaunty/restricted Packages
  404 Not Found
Err http://archive.ubuntu.com jaunty/multiverse Packages
  404 Not Found
Err http://archive.ubuntu.com jaunty/main Packages
  404 Not Found
Err http://archive.ubuntu.com jaunty-updates/universe Packages
  404 Not Found
Err http://archive.ubuntu.com jaunty-updates/restricted Packages
  404 Not Found
Err http://archive.ubuntu.com jaunty-updates/multiverse Packages
  404 Not Found
Err http://archive.ubuntu.com jaunty-updates/main Packages
  404 Not Found
Err http://archive.ubuntu.com jaunty-security/universe Packages
  404 Not Found
Err http://archive.ubuntu.com jaunty-security/restricted Packages
  404 Not Found
Err http://archive.ubuntu.com jaunty-security/multiverse Packages
  404 Not Found
Err http://archive.ubuntu.com jaunty-security/main Packages
  404 Not Found
Err http://archive.ubuntu.com jaunty-backports/universe Packages
  404 Not Found
Err http://archive.ubuntu.com jaunty-backports/multiverse Packages
  404 Not Found
Err http://archive.ubuntu.com jaunty-backports/restricted Packages
  404 Not Found
Err http://archive.ubuntu.com jaunty-backports/main Packages
  404 Not Found
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages  404 Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages  404 Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages  404 Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages  404 Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages  404 Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages  404 Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages  404 Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages  404 Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages  404 Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages  404 Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages  404 Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages  404 Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/binary-i386/Packages  404 Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/binary-i386/Packages  404 Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/binary-i386/Packages  404 Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/binary-i386/Packages  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by zvacet on 2009-08-11
```
cat /etc/apt/sources.list
```

Post it here.

---

### Post by slakkie on 2009-08-11
Seems like you have no DNS servers specified or your internet connection is gone.

Could you please post the output of the following commands:

```

cat /etc/resolv.conf
ifconfig -a
dig a archive.ubuntu.com

```

---

