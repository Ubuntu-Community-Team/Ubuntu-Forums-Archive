---
title: "Ubuntu 9.04 boot problems"
date: 2009-10-14
forum: Installation &amp; Upgrades
---

### Post by triathlaterob on 2009-10-14
I recently installed Ubuntu 9.04 on an old HP Pavillion 423.uk.
 
After the Ubuntu logo and loading bar screen disappear, nothing happens.
 
I reboot into recovery mode, select repair broken packages and get the following,
 
w:failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/release.gpg)
could not resolve 'gb.archive.ubuntu.com'
 
w:failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/release.gpg)
could not resolve 'gb.archive.ubuntu.com
 
w: failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/release.gpg](http://security.ubuntu.com/ubuntu/dists/jaunty-security/release.gpg)
could not resolve 'security.ubuntu.com
 
W: some index files failed to download, they have been ignored, or old ones used instead.
 
W: you may want to run apt-get update to correct these problems.
 
I then resume normal boot, Ubuntu loads and works ok.
 
I have used terminal and run sudo apt-get update and sudo apt-get upgrade but it doesn't seem to help.
 
I'm new to Ubuntu and not sure what to do, can anyone help?
 
Many thanks.
 
Rob

---

### Post by zvacet on 2009-10-14
In system>admin>software sources change server and see if it help.

---

