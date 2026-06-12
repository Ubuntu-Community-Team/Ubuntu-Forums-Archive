---
title: "installation"
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by affran on 2009-07-15
Heloo! I am affran. I have installed ubuntu 9.04 from a usb drive with vist. Whenever i try to upgrade packages through add/remove, synaptic, or through the terminal i get the following errors. Please, Help!:cry::cry::cry::cry:
GPG error: [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) jaunty Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>GPG error: [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) jaunty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-amd64/Packages.bz2](http://bd.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-amd64/Packages.bz2)  Sub-process bzip2 returned an error code (2)

---

### Post by wojox on 2009-07-15
```


sudo bash

apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update

```

```
gpg --export --armor 40976EAF437D05B5 | sudo apt-key add
```

---

### Post by affran on 2009-07-15
whaen i entered

sudo bash


apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update

after few seconds.................................

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)/dists/jaunty/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)/dists/jaunty/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-amd64/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-amd64/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-amd64/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-amd64/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.
root@affran-laptop:/var/lib/apt#

---

