---
title: "Installation script for Brother printers"
date: 2011-12-20
forum: Hardware
---

### Post by demonipuch on 2011-12-20
Hi all,

I wrote a script in bash intending to facilitate the installation of drivers for Brother printers. I posted it on the French community forum a while ago ([http://forum.ubuntu-fr.org/viewtopic.php?id=652931](http://forum.ubuntu-fr.org/viewtopic.php?id=652931)) and wanted to share it with you.

All you need is to do is run the script and answer a few questions, the script will handle the rest for you : prerequisites installation, drivers download and installation.

Dependency : [zenity]("apt://zenity") (which should be installed by default with Ubuntu)

How to get the script and run it :

```
wget http://demonipuch.free.fr/brother.tar.gz
tar zxvf brother.tar.gz
cd brother
chmod +x install.sh
sudo ./install.sh
```If you have any questions/suggestions, please let me know.

---

### Post by hlmai on 2011-12-21
it works fine on natty 11.10

many thanks

---

### Post by demonipuch on 2011-12-21
Hi hlmai

You either mean oneiric 11.10 or natty 11.04 ;)
Anyway thanks for the feedback :)

---

