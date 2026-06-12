---
title: "install Adobe Flash Player version 10.0.22.87"
date: 2009-06-22
forum: Installation &amp; Upgrades
---

### Post by jeff_flynn on 2009-06-22
I'm trying to install Adobe Flash Player version 10.0.22.87 Linux YUM
it downloads ok, but once the Archive Manager opens, this pops up.

Could not open "adobe-release-i386-1.0-1.noarch.rpm"

Archive type not supported.


:confused:

---

### Post by masux594 on 2009-06-22
Try this 
```
sudo apt-get install flashplugin-installer flashplugin-nonfree
```
Sysc, A

---

### Post by jeff_flynn on 2009-06-22
it says i have newest version

---

### Post by tommcd on 2009-06-22
First, make sure you uninstall any previous Flash or Gnash versions that you may have installed from the Ubuntu repos.
Then download the Flash .tar.gz file to your home directory from here:
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
Then untar it from the terminal:
```
tar -xvzf install_flash_player_10_linux.tar.gz
```
(or whatever the file is named exactly).
Then cd into the install_flash_player_10_linux/ directory:
```
cd install_flash_player_10_linux/
```
Then copy the libflashplayer.so file to /usr/lib/mozilla/plugins:
```
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/
```
Then restart Firefox.

EDIT: This will get you the latest version directly from adobe.com.

---

### Post by her0in on 2009-06-22
> **tommcd said:**
> First, make sure you uninstall any previous Flash or Gnash versions that you may have installed from the Ubuntu repos.
Then download the Flash .tar.gz file to your home directory from here:
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
Then untar it from the terminal:
```
tar -xvzf install_flash_player_10_linux.tar.gz
```(or whatever the file is named exactly).
Then cd into the install_flash_player_10_linux/ directory:
```
cd install_flash_player_10_linux/
```Then copy the libflashplayer.so file to /usr/lib/mozilla/plugins:
```
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/
```Then restart Firefox.

EDIT: This will get you the latest version directly from adobe.com.


thank you very much, if it wasn't for your well-typed out answer i would have never gotten it installed as a brand new user!

---

