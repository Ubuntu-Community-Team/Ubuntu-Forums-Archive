---
title: "Update manager error"
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by saxasm on 2009-02-26
I get these errors when i try to check for new updates.
```
W: GPG error: http://mirror.noreply.org hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CFF71CB3AFA44BDD
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DCCB2270E7716B13
```
I have a rough idea what is wrong but im absolutely clueless as of how to solve it.

---

### Post by Partyboi2 on 2009-02-26
Open a terminal (Applications>Accessories>Terminal) then type
```
gpg --keyserver subkeys.pgp.net --recv 94C09C7F
gpg --export 94C09C7F | sudo apt-key add -
```

Then
```
gpg --keyserver keyserver.ubuntu.com --recv DCCB2270E7716B13
gpg --export --armor DCCB2270E7716B13 | sudo apt-key add -
```

---

