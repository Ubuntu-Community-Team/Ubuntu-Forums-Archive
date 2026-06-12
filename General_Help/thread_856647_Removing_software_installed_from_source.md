---
title: "Removing software installed from source"
date: 2008-07-11
forum: General Help
---

### Post by barefootsanders on 2008-07-11
Hey everyone,

I installed a few programs from source and being a novice at ubuntu and linux in general I was wondering if there was any easy way to remove them or I have to dive into my file system and remove directories one at a time.

Thanks

---

### Post by ad_267 on 2008-07-11
It depends on the actual application. Usually you can go into the directory where the source code is and do a "sudo make uninstall" to remove the application. Sometimes this doesn't work though.

---

### Post by drs305 on 2008-07-11
If you kept the folder created during the installation you may find a subfolder called *postinst* or something similar which contains a removal script. 

Difficulty uninstalling compiled apps is another reason to use "checkinstall" instead of "make install". It will create a deb file which gets registered within APT and allows for easier removal when that time comes.

---

### Post by ibutho on 2008-07-11
Usually tarballs contain a README or INSTALL file. You can find information for installing and uninstalling the package from this file. In most cases "make uninstall" should work, but a few applications do not have uninstallers or there maybe a different way to remove it e.g. running an uninst script.

---

