---
title: "update trouble"
date: 2009-02-08
forum: Installation &amp; Upgrades
---

### Post by geneh2 on 2009-02-08
I have Ubuntu 8.04 on a Dell C400 and it has been just freezing up.  I run sudo apt-get update and it reads this

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783


I am new so not sure what to do

---

### Post by Partyboi2 on 2009-02-09
Open a terminal (Applications>Accessories>Terminal) and type or paste[FONT=monospace]
[/FONT]```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```
This will  add the gpg key.

---

### Post by geneh2 on 2009-02-09
Thanks!:)

---

