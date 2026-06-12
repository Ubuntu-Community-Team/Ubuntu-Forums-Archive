---
title: "Could Not Download All Repository Indexes"
date: 2009-04-13
forum: Installation &amp; Upgrades
---

### Post by erin_l on 2009-04-13
This is the error I keep receiving when I try updating.

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Some index files failed to download, they have been ignored, or old ones used instead.

*I have checked the following in the Software Sources menu.

Ubuntu Software:
Canonical-supported Open Source Software (main)

Updates:
Important Security Updates (hardy-security)
Recommended Updates (hardy-updates)

I am using Ubuntu 8.04 on a Dell Mini 9.

---

### Post by antikristian on 2009-04-13
Are these repos listed in software sources -> third party repos?

If they are, replace archive.ubuntu.com and security.ubuntu.com with ports.ubuntu.com and try again

If they are not listed in the third parties list, edit /etc/apt/sources.list

---

### Post by antikristian on 2009-04-15
Check the reply from the ubuntu developer here:
[http://ubuntuforums.org/showthread.php?t=1124709](http://ubuntuforums.org/showthread.php?t=1124709)

---

### Post by Partyboi2 on 2009-04-15
> **erin_l said:**
> This is the error I keep receiving when I try updating.

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Some index files failed to download, they have been ignored, or old ones used instead.

*I have checked the following in the Software Sources menu.

Ubuntu Software:
Canonical-supported Open Source Software (main)

Updates:
Important Security Updates (hardy-security)
Recommended Updates (hardy-updates)

I am using Ubuntu 8.04 on a Dell Mini 9.

Open a terminal (Applications>Accessories>Terminal) and open your sources.list with gedit
```
gksu gedit /etc/apt/sources.list
``` then put a # in front of all the ubuntu repo's lines that start with 'deb' then at the bottom of file add these
```
deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted
``` then save the changes and close gedit. Then back in the terminal
```
sudo apt-get update
```If you unsure how to edit your sources.list open a terminal and post the output to ```
cat /etc/apt/sources.list
``` and someone should be able to help you.

---

