---
title: "Update Errors: How do I fix"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by fr0sty on 2009-03-16
Hello. I recently tried to update my ubuntu 8.04 computer and when checking for updates, I got the following errors:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 02FE5F12ADDE29B2

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7C5BAD1320A0D1DA

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783


I know your supposed to somehow grab a public key somehow and download it through terminal, but have no clue on how to do this. All help is very deeply appreciated. Thanks!

---

### Post by Partyboi2 on 2009-03-16
Open a terminal  and add the keys
```
gpg --keyserver keyserver.ubuntu.com --recv  02FE5F12ADDE29B2
gpg --export --armor 02FE5F12ADDE29B2  | sudo apt-key add -
```
then the same for the next one
```
gpg --keyserver keyserver.ubuntu.com --recv 7C5BAD1320A0D1DA
gpg --export --armor 7C5BAD1320A0D1DA | sudo apt-key add -
```

then for the medibuntu one
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by fr0sty on 2009-03-16
Thank you. That made my day.

---

