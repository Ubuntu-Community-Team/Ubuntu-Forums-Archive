---
title: "'Could not download the upgrades' when upgrading from 9.04 to 9.1"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by Guicun on 2009-11-03
I have tried 4 times to upgrade from 9.04 to 9.10, but stops at latests files with the next message:

Could not download the upgrades

These are the failed files

Failed to fetch [http://es.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/libpython2.6_2.6.4-0ubuntu1_i386.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/libpython2.6_2.6.4-0ubuntu1_i386.deb) 404 Not Found
Failed to fetch [http://es.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/python2.6_2.6.4-0ubuntu1_i386.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/python2.6_2.6.4-0ubuntu1_i386.deb) 404 Not Found
Failed to fetch [http://es.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/python2.6-minimal_2.6.4-0ubuntu1_i386.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/python2.6-minimal_2.6.4-0ubuntu1_i386.deb) 404 Not Found
Failed to fetch [http://es.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.126.6.1_all.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.126.6.1_all.deb) 404 Not Found
Failed to fetch [http://es.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-core_0.126.6.1_i386.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-core_0.126.6.1_i386.deb) 404 Not Found
Failed to fetch [http://es.archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/python-ubuntuone-client_1.0.2-0ubuntu2_all.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/python-ubuntuone-client_1.0.2-0ubuntu2_all.deb) 404 Not Found
Failed to fetch [http://es.archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/ubuntuone-client_1.0.2-0ubuntu2_all.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/ubuntuone-client_1.0.2-0ubuntu2_all.deb) 404 Not Found
Failed to fetch [http://es.archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/ubuntuone-client-gnome_1.0.2-0ubuntu2_i386.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/ubuntuone-client-gnome_1.0.2-0ubuntu2_i386.deb) 404 Not Found


How i have to proceed to follow ?

Thanks

---

### Post by mac9416 on 2009-11-03
Try running 'sudo apt-get update' in the terminal before upgrading.

---

### Post by Guicun on 2009-11-04
Thanks.

Instead of your solution I change the parameters of the Upgrade Manager in order to download from another server, and don't fail !

Regards from Catalonia

---

