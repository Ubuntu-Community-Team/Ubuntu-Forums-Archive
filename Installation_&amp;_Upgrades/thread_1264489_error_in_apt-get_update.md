---
title: "error in apt-get update"
date: 2009-09-12
forum: Installation &amp; Upgrades
---

### Post by vicky.it.bhu on 2009-09-12
After i run the *sudo apt-get update* command i get this message at the end. What does this mean ?? How can i solve it ??
```

Hit http://archive.ubuntu.com jaunty-updates/multiverse Packages                                   
Hit http://archive.ubuntu.com jaunty-updates/restricted Packages                                   
Fetched 1064B in 9s (117B/s)                                                                       
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B2F1D0A461B3A0B1
W: You may want to run apt-get update to correct these problems

```

---

### Post by Partyboi2 on 2009-09-12
Hi, it means you have not added the gpg key, to do this open a terminal and
```
gpg --keyserver keyserver.ubuntu.com --recv B2F1D0A461B3A0B1
gpg --export --armor B2F1D0A461B3A0B1  | sudo apt-key add -
```
then
```
sudo apt-get update
```

---

