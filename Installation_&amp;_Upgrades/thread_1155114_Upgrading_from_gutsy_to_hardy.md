---
title: "Upgrading from gutsy to hardy"
date: 2009-05-10
forum: Installation &amp; Upgrades
---

### Post by etali on 2009-05-10
Hi all,

I was asking for help with something in the server forums, and I was told that gutsy is no longer supported.

I'd like to upgrade to hardy (at the least), but I'm not sure how to do it.  The server in question is a VPS, and I don't have physical access to it - I was going to follow a tutorial ([http://www.codedifferent.com/2008/05/04/update-ubuntu-server-710-gutsy-gibbon-to-804-lts-hardy-heron-via-terminal/](http://www.codedifferent.com/2008/05/04/update-ubuntu-server-710-gutsy-gibbon-to-804-lts-hardy-heron-via-terminal/)) but I don't have update-manager-core, and the repositories I'm using aren't working any more.

Any advice would be much appreciated.

---

### Post by cariboo on 2009-05-10
You can go [here]("http://old-releases.ubuntu.com/releases/") and install update-manager-core, then follow the howto.

---

### Post by spd106 on 2009-05-10
Hello,

You can still get the update-manager-core package from the archives at 
[http://old-releases.ubuntu.com/ubuntu/pool/main/u/update-manager/](http://old-releases.ubuntu.com/ubuntu/pool/main/u/update-manager/)

It looks like you need version 0.81, according to the listing at [http://old-releases.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages](http://old-releases.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages)



For reference:
[https://help.ubuntu.com/8.04/serverguide/C/installing-upgrading.html](https://help.ubuntu.com/8.04/serverguide/C/installing-upgrading.html)
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by etali on 2009-05-11
Thanks!  Remote upgrades are pretty nerve-wracking, but that's one upgraded server now :)  I can't believe I missed the old-releases pages last night.

---

