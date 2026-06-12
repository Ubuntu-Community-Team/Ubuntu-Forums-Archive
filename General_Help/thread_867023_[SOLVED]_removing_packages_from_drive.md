---
title: "[SOLVED] removing packages from drive"
date: 2008-07-22
forum: General Help
---

### Post by flytripper on 2008-07-22
hi i would like to reinstall wine from the repository but it always just uses the previous package apt downloaded. could you tell me where i can find it in my file structure so i can delete it please..

---

### Post by coffeecat on 2008-07-22
> **flytripper said:**
> where i can find it in my file structure so i can delete it please..

Well, I can, but first....

Have you tried clicking on the 'Reload' button in Synaptic, so that it downloads the latest package information? Synaptic will only install the latest version it knows about, so if you don't reload, it will just use the package for the version it knows about. And if you reload and it still uses the same version, then that's the latest that is available.

Having said all that, the location of stored .deb files is /var/cache/apt/archives . Alternatively, you could choose 'Mark for complete removal' from Synaptic. Then, if you reinstall it will have to download the .deb package.

---

### Post by todak on 2008-07-22
If apt keeps reinstalling the version of wine it downloaded to your drive, it means there is not a newer version available. However, if you must remove it ```
sudo apt-get clean wine
``` will remove it and then you will download it from the repository next time you want to install it.

---

### Post by flytripper on 2008-07-22
thanks.. i tend to use terminal for installing and removing. will look at synaptic
.

---

