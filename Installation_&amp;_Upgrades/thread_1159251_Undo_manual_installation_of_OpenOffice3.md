---
title: "Undo manual installation of OpenOffice3"
date: 2009-05-14
forum: Installation &amp; Upgrades
---

### Post by BlueElk on 2009-05-14
I have just upgraded to jaunty, from intrepid, and was happy to find that OpenOffice3 is included. The thing is, while I was using intrepid I installed OO3 by downloading and unpacking a .tar.gz file, and running the command

sudo dpkg -i *.deb

in the (extracted) subdirectory DEBS filled with .deb files.

Does anyone know how I can undo this manual installation (basically, how do I undo "sudo dpkg -i *.deb")?

(The .tar.gz file was OOO300_m9_native_packed-1_sv.9358.tar.gz I think.)

---

### Post by cariboo on 2009-05-14
You should be able to use:

```
sudo apt-get purge openoffice.org
```

openoffice.org, is the meta package that installs open office and it components.

---

### Post by BlueElk on 2009-05-15
```
sudo apt-get purge openoffice.org
```

resulted in

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package openoffice.org is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

Synaptic confirms that openoffice.org is not installed, but it also says that openoffice.org3 (version 3.0.0-9) is installed. That is the version of OO I installed manually under intrepid, which appears to be broken under jaunty. However, I can launch the 3.0.1 version of OO that comes with jaunty (e.g. via the sub menu "Office"). Seems weird to me.

Maybe I should uninstall all OO-packages, and then install the package openoffice.org? Alternatively, uninstall only the OO-packages marked as version 3.0.0-9?

---

### Post by BlueElk on 2009-05-16
Resolved. I guess.

I used synaptic to mark all packages called ooobasis3.0-* for removal, which triggered synaptic to also mark openoffice.org3 for removal. This deleted almost all files from the /opt/openoffice.org3/ (*) directory, and OO version 3.0.1 still works, so it looks like a success. 

(*) My manual installation of OO placed a bunch of files in /opt/openoffice.org3/

Keep your fingers crossed for Malena tonight. =)

---

