---
title: "VLC Player installation"
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by ajbharani on 2008-12-16
Hi ,

I'm planning to install VLC player on my ubuntu (8.10) desktop. I found the packages here [http://packages.ubuntu.com/intrepid/vlc](http://packages.ubuntu.com/intrepid/vlc).

1. Is this the correct one to use?
2. Should I have to download all the dependant modules seperately or not?

Thanks.

---

### Post by Partyboi2 on 2008-12-16
If you are connected to the internet you can search Add/Remove (Applications>Add/Remove) for vlc or you can open a terminal (Applications>Accessories>Terminal) and install with
```
sudo apt-get install vlc
```If you do not have internet you will need to installed the dependencies that are required.

---

### Post by ibutho on 2008-12-16
It would probably be easier to use the package manager. Go to System -> Administration -> Software Sources and enable the multiverse and universe repository. After that go to System -> Administration -> Synaptic. update the software sources and then search for vlc and select it for installation.

---

### Post by ajbharani on 2008-12-16
> **Partyboi2 said:**
> If you are connected to the internet you can search Add/Remove (Applications>Add/Remove) for vlc or you can open a terminal (Applications>Accessories>Terminal) and install with
```
sudo apt-get install vlc
```If you do not have internet you will need to installed the dependencies that are required.

No. I do not have an internet connection at my place. I can access internet from somewhere else.

---

### Post by Partyboi2 on 2008-12-16
You could try using "[[COLOR=Blue]generate package download script[/COLOR]]("https://help.ubuntu.com/community/Synaptic/PackageDownloadScript")" or [[COLOR=Blue]keryx[/COLOR]]("http://keryx.betaserver.org/")

---

### Post by albinootje on 2008-12-16
> **ajbharani said:**
> No. I do not have an internet connection at my place. I can access internet from somewhere else.

This is also an option when you have no internet : [http://aptoncd.sourceforge.net](http://aptoncd.sourceforge.net)

---

