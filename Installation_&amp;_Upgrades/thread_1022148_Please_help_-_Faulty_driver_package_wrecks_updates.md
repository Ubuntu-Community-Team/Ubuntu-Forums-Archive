---
title: "Please help - Faulty driver package wrecks updates"
date: 2008-12-26
forum: Installation &amp; Upgrades
---

### Post by ÄlveKatt on 2008-12-26
E: The package mfc9180lpr needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

The printer package was downloaded from the official brother site.
[http://solutions.brother.com/linux/en_us/download_prn.html#MFC-9180]("http://solutions.brother.com/linux/en_us/download_prn.html#MFC-9180")

Now I can't update, can't remove, can't reinstall. Neither update manager nor Synaptic will start because of this package. Please help?

Version is 8.10

---

### Post by ÄlveKatt on 2008-12-26
I forgot to add the Ubuntu version in the last post. It is 8.10.

---

### Post by Partyboi2 on 2008-12-26
This is what worked for me.
Open a terminal and try
```
sudo dpkg --remove --force-remove-reinstreq mfc9180lpr
```
If that does not work then open up //var/lib/dpkg/status
```
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.backup
```
```
gksu gedit /var/lib/dpkg/status
```
search for mfc9180lpr, should look something like this: 
> Package: mfc9180lpr
Status: deinstall reinstreq half-installed
Maintainer: Brother Industries, Ltd.
Architecture: i386
Version: 1.1.2-1
Description: Brother lpr Printer Definitions
 Copyright: 2003 Brother Industries, Ltd. All Rights Reserved
 Brother printer Driver
delete it and save.
Then back in the terminal
```
sudo apt-get -f install
sudo dpkg --configure -a
```

---

### Post by ÄlveKatt on 2008-12-27
Thank you so very much. That did it.

---

### Post by ÄlveKatt on 2008-12-27
Oh, and there was no faulty driver. I just did it wrong...

Though it can't be good that the update thingie is so easy to inadvertently break

---

