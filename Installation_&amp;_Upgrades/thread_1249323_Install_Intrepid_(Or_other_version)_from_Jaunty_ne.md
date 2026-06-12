---
title: "Install Intrepid (Or other version) from Jaunty netinstall"
date: 2009-08-25
forum: Installation &amp; Upgrades
---

### Post by SATA on 2009-08-25
Hi All,

Is there a way I can install Intrepid Ibex from the Jaunty Jackalope netinstall image?

I have my system booting the installer over the network and it installs jaunty fine (Using Preseeding)

If I have this in my preseed file, installation goes perfectly
```
# Suite to install.
d-i mirror/suite string jaunty
# Suite to use for loading installer components (optional).
d-i mirror/udeb/suite string jaunty

```Yet, if I change the above to:
```
# Suite to install.
d-i mirror/suite string intrepid
# Suite to use for loading installer components (optional).
d-i mirror/udeb/suite string intrepid

```The installer moans about kernel modules not being found and installation fails, which I dont understand why, does the ubuntu installer not use debootstrap ?
I dont understand why it would moan about kernel modules for a kernel its not currently running and hasn't even attempted to install yet.

I _**REALLY**_ dont want to have seperate kernel's and initrd's for each suite just so I can netinstall them.

I would have thought newer netinstall images would have backwards compatibility?

If theres something im missing out, please let me know.

Relevant lines from ubuntu.cfg file:
```

label install-kubuntu-lmce
  MENU LABEL ^Install Kubuntu (Intrepid)
  KERNEL images/ubuntu-netboot/linux
  APPEND url=http://10.0.0.1/preseed/kubuntu810.cfg initrd=images/ubuntu-netboot/initrd.gz vga=normal locale=en_NZ setup/layoutcode=en_NZ console-setup/layoutcode=us netcfg/get_hostname= -- quiet

label install-ubuntu
  MENU LABEL ^Install Ubuntu (Latest)
  KERNEL images/ubuntu-netboot/linux
  APPEND url=http://10.0.0.1/preseed/ubuntu-latest.cfg initrd=images/ubuntu-netboot/initrd.gz vga=normal locale=en_NZ setup/layoutcode=en_NZ console-setup/layoutcode=us netcfg/get_hostname= -- quiet

```

---

