---
title: "Installation/Downloading problem"
date: 2009-10-14
forum: Installation &amp; Upgrades
---

### Post by yashas.d on 2009-10-14
Whenever i try to install any new application, the following error is shown....also it says that...."cannot be installed on your computer type (i386)"....
What shud i do? Need help badly....even effects are not working as i cannot download the pakages....

Either the application requires special hardware features or the vendor decided to not support your computer type.
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages.bz2)  Hash Sum mismatch
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages.bz2)  Hash Sum mismatch
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources.bz2)  Hash Sum mismatch
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources.bz2)  Hash Sum mismatch
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages.bz2](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages.bz2)  Hash Sum mismatch
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages.bz2](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages.bz2)  Hash Sum mismatch
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages.bz2](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages.bz2)  Hash Sum mismatch
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages.bz2](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages.bz2)  Hash Sum mismatch
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources.bz2](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources.bz2)  Hash Sum mismatch
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources.bz2](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources.bz2)  Hash Sum mismatch
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources.bz2](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources.bz2)  Hash Sum mismatch
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources.bz2](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources.bz2)  Hash Sum mismatch
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages.bz2](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages.bz2)  Hash Sum mismatch
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages.bz2](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages.bz2)  Hash Sum mismatch
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages.bz2](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages.bz2)  Hash Sum mismatch
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages.bz2](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages.bz2)  Hash Sum mismatch
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources.bz2](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources.bz2)  Hash Sum mismatch
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources.bz2](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources.bz2)  Hash Sum mismatch
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources.bz2](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources.bz2)  Hash Sum mismatch
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources.bz2](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources.bz2)  Hash Sum mismatch
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by QIII on 2009-10-14
Try the main server.

---

### Post by prshah on 2009-10-14
> **yashas.d said:**
> Some index files failed to download, they have been ignored, or old ones used instead.

As a first step, try updating your repos (I assume you can use the Internet?) Open a terminal (Applications-Accessories-Terminal) and give the command ```
sudo apt-get update
``` If this completes successfully, then try installing a package, otherwise, post back the errors along with the below information.

If that fails with the same message about computer type, what type of ubuntu are you using (amd64 or i386)? If you do not know, give the below command in the terminal```
uname -m
``` and post back the result.

---

