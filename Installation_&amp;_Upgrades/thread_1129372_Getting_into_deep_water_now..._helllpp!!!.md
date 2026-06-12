---
title: "Getting into deep water now... helllpp!!!"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by dougalkerr on 2009-04-18
Tried sudo apt-get update to help with authenticating key problems in Software Sources. See copied Terminal advice as follows;

Reading package lists... Done
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: GPG error: [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: You may want to run apt-get update to correct these problems

Please help a novice before it gets desperate... thanks.

---

### Post by zvacet on 2009-04-18
In **system>admin>software sources** try to change server.I tried all your links and they work for me.

---

### Post by dougalkerr on 2009-04-20
This was posted by bigtomrodney off the Linux Forums site and it works a treat;

gpg --keyserver keyserver.ubuntu.com --recv 40976EAF437D05B5
gpg --export --armor 40976EAF437D05B5 | sudo apt-key add -
gpg --keyserver keyserver.ubuntu.com --recv 60D11217247D1CFF
gpg --export --armor 60D11217247D1CFF | sudo apt-key add -
sudo apt-get update

---

