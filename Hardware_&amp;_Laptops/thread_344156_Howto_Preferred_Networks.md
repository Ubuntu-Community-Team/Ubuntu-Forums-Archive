---
title: "Howto: Preferred Networks"
date: 2007-01-22
forum: Hardware &amp; Laptops
---

### Post by scubanator87 on 2007-01-22
I was having some problems with my network manager trying to connect to preferred networks other than my own when i found this [Debian User Forum Post.]("http://forums.debian.net/viewtopic.php?p=43551&sid=1348b9998746d42ce64f2fc05069c174")


All you need to do is fire up a terminal and:

```
cd .gconf/system/networking/wireless/networks/
```
 
then remove the networks you don't want by replacing **<ESSID> **with unwanted network names.

```
ls 
rm -rf <ESSID>/
```

Restart network manager
```

sudo killall NetworkManager
sudo NetworkManager
```

then it should only be connecting to the preferred networks you left in that folder.

---

### Post by ASUmusicMAN on 2007-02-02
Thanks :)

---

