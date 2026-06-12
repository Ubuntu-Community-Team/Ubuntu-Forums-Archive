---
title: "upgrade from 8.10 to 9.04 hangs while fetching packages"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by eskararriba on 2009-10-29
while everybody seems to be fixing issues with the upgrade to 9.10 beta, I'm having trouble with the **upgrade from 8.10 to 9.04 **- 

the update manager hangs after having downloaded all but the last package. after I pressed cancel, the report it gave me was: 

"Failed to fetch http://mx.archive.ubuntu.com/ubuntu/pool/main/c/cdparanoia/cdparanoia_3.10.2+debian-5_i386.deb"

update manager then offers me a partial install, which isn't really what I was looking for. 
now that I shut down and opened the update manager again, I got a message that goes: 

"W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9423A34CCA967634"

any idea what I could do to upgrade to 9.04? 
thanks a lot

---

### Post by eskararriba on 2009-10-29
ok, sorry, think I found the solution all by myself ... just restarted the upgrade and things seem to go reasonably well;)

---

