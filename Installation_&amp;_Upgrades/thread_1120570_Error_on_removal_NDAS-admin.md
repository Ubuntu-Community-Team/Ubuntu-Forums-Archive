---
title: "Error on removal NDAS-admin"
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by rjg_1966 on 2009-04-09
I am trying to remove (and reinstall) NDAS on Intrepid, however get the following error message from the Synaptic Package Manager

   E: ndas-admin: subprocess pre-removal script returned error exit status 2

If I try to use sudo apt-get install ndas-admin, I get the following error messages:

    Setting up ndas-admin (1.0.3-101) ...
    update-rc.d: /etc/init.d/ndas: file does not exist
    /bin/sh: Can't open /etc/init.d/ndas
    dpkg: error processing ndas-admin (--configure):
    subprocess post-installation script returned error exit status 2
    Errors were encountered while processing:
    ndas-admin
    E: Sub-process /usr/bin/dpkg returned an error code (1)

Any suggestions - I'd like to either remove is completely prior to an attempt at a patched reinstall!

thanks

---

