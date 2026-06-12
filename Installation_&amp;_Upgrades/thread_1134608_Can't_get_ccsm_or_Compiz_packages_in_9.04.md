---
title: "Can't get ccsm or Compiz packages in 9.04"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by ubigT on 2009-04-23
I have a fresh install of 9.04 and I cannot install ccsm or anything else from compiz..... what the hell? I get errors like this:

W: Failed to fetch [http://ubuntu.cbn.net.id/Ubuntu/pool/universe/c/compiz-fusion-plugins-unsupported/compiz-fusion-plugins-unsupported_0.7.8-0ubuntu1_i386.deb](http://ubuntu.cbn.net.id/Ubuntu/pool/universe/c/compiz-fusion-plugins-unsupported/compiz-fusion-plugins-unsupported_0.7.8-0ubuntu1_i386.deb)
  404 Not Found


W: Failed to fetch [http://ubuntu.cbn.net.id/Ubuntu/pool/universe/c/compizconfig-python/python-compizconfig_0.8.2-0ubuntu1_i386.deb](http://ubuntu.cbn.net.id/Ubuntu/pool/universe/c/compizconfig-python/python-compizconfig_0.8.2-0ubuntu1_i386.deb)
  404 Not Found


W: Failed to fetch [http://ubuntu.cbn.net.id/Ubuntu/pool/universe/c/compizconfig-settings-manager/compizconfig-settings-manager_0.8.2-0ubuntu1_all.deb](http://ubuntu.cbn.net.id/Ubuntu/pool/universe/c/compizconfig-settings-manager/compizconfig-settings-manager_0.8.2-0ubuntu1_all.deb)
  404 Not Found


Anyone else had this?  I have searched the forums and don't seem to see this problem anywhere else....

---

### Post by yeats on 2009-04-23
They may have rearranged their server file structure as Jaunty came available.  If you click on the link, you'll see that indeed, there is no page available.  Try going to the main site:
[URL="http://ubuntu.cbn.net.id/"]
http://ubuntu.cbn.net.id/[/URL]

then digging down to the correct file, then add the link (or download directly from it).

---

### Post by ubigT on 2009-04-24
Dug down and found this:

[http://ubuntu.cbn.net.id/Ubuntu/pool/main/c/compizconfig-settings-manager/](http://ubuntu.cbn.net.id/Ubuntu/pool/main/c/compizconfig-settings-manager/)

but it's empty! WTF? So I just can't have it? I want my cube back! Jaunty is awesome so far other than this...

EDIT:

Found this:
[http://ubuntu.cbn.net.id/Ubuntu/pool/universe/c/compizconfig-settings-manager/](http://ubuntu.cbn.net.id/Ubuntu/pool/universe/c/compizconfig-settings-manager/)

but it's for 7.8 not 8.2

---

### Post by Partyboi2 on 2009-04-24
Open up Software Sources and try changing the download server to another one.

---

### Post by drs305 on 2009-04-24
I installed simple-ccsm a few hours ago without issue from the U.S. mirror.cc.columbia.edu server. I just checked and it and compiz are both available - at least the 64-bit versions.

---

### Post by ubigT on 2009-04-24
Oh thank god, it works.

thanks everyone!

---

