---
title: "Installing fingerprint-gui in Bionic"
date: 2018-04-14
forum: Hardware
---

### Post by volkerbradley on 2018-04-14
After "sudo apt-get install libbsapi policykit-1-fingerprint-gui fingerprint-gui", there is an error message: "The following packages have unmet dependencies:fingerprint-gui : Depends: libqca2-plugin-ossl but it is not installable. E: Unable to correct problems, you have held broken packages."
Bionic documentation shows that libqca2-plugin-ossl has been removed. After "sudo apt-get install libqca2-plugin-ossl" the message states: "Package libqca2-plugin-ossl is not available, but is referred to by another package. The following packages replace it:
libqca2-plugins:i386 libqca2-plugins
How can fingerprint-gui be installed using libqca2-plugins?
Thanks.

---

