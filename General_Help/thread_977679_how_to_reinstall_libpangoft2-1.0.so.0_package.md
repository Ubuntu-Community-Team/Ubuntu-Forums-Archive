---
title: "how to reinstall libpangoft2-1.0.so.0 package?"
date: 2008-11-10
forum: General Help
---

### Post by raiwo on 2008-11-10
after updating something went wrong & my macine is missing above mentioned file. And gnome desktop is not working anymore.

i tried apt-get update, apt get upgrade, no new packages were found. The i tried apt-get install libpangoft2-1.0.so.0 put i just got "couldn't find package..."

so where to get that package or how to fix my machine?

---

### Post by blacky667 on 2008-11-10
libpangoft2-1.0.so.0 is contained in the package libpango1.0-0, so a ```
apt-get install libpango1.0-0
``` should work. If it was installed during the upgrade but only partial you should try it with the option --reinstall

---

### Post by raiwo on 2008-11-10
itried to apt-get install libpango1.0-0 & my machine says latest installed etc... so i did remove & then install it again. Now gmd is gone completely & when trying to intall it again it just says no can do. 

Is there any way to install ubuntu completely again from command line?

---

### Post by blacky667 on 2008-11-12
I guess you have encountered a dependency problem. You can check it with "apt-get check" and if apt report any problems try "apt-get upgrade" to install missing packages and resolve the dependency problems.
If apt reports any unconfigured packages in this process you can configure them by hand with "dpkg --configure --pending"

Don't know of any way to reinstall from commandline but you can use the live-cd or network-install to reinstall ubuntu of course

---

