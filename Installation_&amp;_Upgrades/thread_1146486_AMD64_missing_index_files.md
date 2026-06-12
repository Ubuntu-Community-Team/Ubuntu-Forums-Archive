---
title: "AMD64 missing index files?"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by Salix0210 on 2009-05-02
In "update manager" of 8.04.2 for the "check" button I receive the following message (partly hu, partly en).

> Sikertelen letöltés: [http://hu.archive.ubuntu.com/ubuntu/dists/hardy/Release](http://hu.archive.ubuntu.com/ubuntu/dists/hardy/Release) Unable to find expected entry web/binary-amd64/Packages in Meta-index file (malformed Release file?)
Sikertelen letöltés: [http://hu.archive.ubuntu.com/ubuntu/dists/hardy-updates/Rele](http://hu.archive.ubuntu.com/ubuntu/dists/hardy-updates/Rele)... Unable to find expected entry web/binary-amd64/Packages in Meta-index file (malformed Release file?)
Sikertelen letöltés: [http://security.ubuntu.com/ubuntu/dists/hardy-security/Relea](http://security.ubuntu.com/ubuntu/dists/hardy-security/Relea)... Unable to find expected entry web/binary-amd64/Packages in Meta-index file (malformed Release file?)
Néhány index fájl letöltése meghiúsult, ezeket mell&#337;zöm vagy régi változatukat használom.


I think the same stops me from upgrading to 8.10. The exact message I get if I start upgrading from 8.04 to 8.10 is following.

> W:Sikertelen letöltés: [http://hu.archive.ubuntu.com/ubuntu/dists/intrepid/Release](http://hu.archive.ubuntu.com/ubuntu/dists/intrepid/Release)  Unable to find expected entry  web/binary-amd64/Packages in Meta-index file (malformed Release file?)
 , W:Sikertelen letöltés: [http://hu.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release](http://hu.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release)  Unable to find expected entry  web/binary-amd64/Packages in Meta-index file (malformed Release file?)
 , W:Sikertelen letöltés: [http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release](http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release)  Unable to find expected entry  web/binary-amd64/Packages in Meta-index file (malformed Release file?)
 , E:Néhány index fájl letöltése meghiúsult, ezeket mell&#337;zöm vagy régi változatukat használom.

Any idea? What should I do?

---

### Post by taurus on 2009-05-02
Go into System -> Administration -> Software Sources and switch to another server.  Try the Main Server if you wish.

---

### Post by Salix0210 on 2009-05-02
Doesn't seem to solve the problem. 

> Sikertelen letöltés: [http://archive.ubuntu.com/ubuntu/dists/hardy/Release](http://archive.ubuntu.com/ubuntu/dists/hardy/Release)  Unable to find expected entry  web/binary-amd64/Packages in Meta-index file (malformed Release file?)
Sikertelen letöltés: [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  Unable to find expected entry  web/binary-amd64/Packages in Meta-index file (malformed Release file?)
Sikertelen letöltés: [http://archive.ubuntu.com/ubuntu/dists/hardy-security/Release](http://archive.ubuntu.com/ubuntu/dists/hardy-security/Release)  Unable to find expected entry  web/binary-amd64/Packages in Meta-index file (malformed Release file?)

---

### Post by Salix0210 on 2009-05-03
The solution seems to be

[http://ubuntuforums.org/showthread.php?t=742624](http://ubuntuforums.org/showthread.php?t=742624)

---

