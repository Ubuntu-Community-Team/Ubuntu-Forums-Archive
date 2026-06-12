---
title: "Intrepid 8.10 install on ESXi 3.5u3 with open-vm-tools"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by jzimmerman on 2009-03-13
Does someone have a walk-through for this using the "open-vm-tools" package in the repository.

I have the open-vm-tools installed but the modules (e.g. vmxnet, etc...) never get built and therefore do not load.

I am looking to complete this install with the vmware tools from the repository without having to monkey around with downloading tar files from the open-vm-tools project or using the tar ball from the ESXi server.

Is this not supposed to work this way?

Any help is appreciated.

---

### Post by jzimmerman on 2009-03-13
Got it working by following this....

[http://www.gorillapond.com/2009/03/09/install-vmware-tools-on-ubuntu-linux-reborn/](http://www.gorillapond.com/2009/03/09/install-vmware-tools-on-ubuntu-linux-reborn/)

The piece I was missing is that for some reason the modules are built when the packages are installed and configured.  You must use the module-assist commands to build the modules first.

Not ideal, but I didn't have to use any of the tarballs.

---

