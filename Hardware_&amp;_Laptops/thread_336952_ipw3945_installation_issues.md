---
title: "ipw3945 installation issues"
date: 2007-01-12
forum: Hardware &amp; Laptops
---

### Post by uterrorista on 2007-01-12
i'm following this tutorial:
```
$ sudo apt-get install linux-headers-$(uname -r) wireless-tools

Downloading latest version of ieee802111:

$ cd /usr/src
$ sudo wget ttp://prdownloads.sourceforge.net/ieee80211/ieee80211-1.2.15.tgz?download

installing ieee80211:

$ sudo tar xvfz ieee80211-1.2.15.tgz
$ cd ieee80211-1.2.15
$ sudo sh remove-old
$ sudo make IEEE80211_INC=/usr/include
$ sudo make install
$ cd ..

installing driver ip3945 in /usr/src:

$ sudo wget http://umn.dl.sourceforge.net/sourceforge/ipw3945/ipw3945-1.1.0.tgz
$ cd /usr/src
$ sudo tar xvfz ipw3945-1.1.0.tgz
$ cd ipw3945-1.1.0
$ sudo ./unload   [COLOR="Red"] #Error[/COLOR]
$ sudo make IEEE80211_IGNORE_DUPLICATE=y

Installing firmware and daemon:

$ cd ..
$ sudo wget http://bughost.org/ipw3945/ucode/ipw3945-ucode-1.13.tgz
$ sudo tar xvfz ipw3945-ucode-1.13.tgz
$ cd ipw3945-ucode-1.13
$ sudo cp ipw3945.ucode /lib/firmware/
$ cd ..

$ sudo wget http://bughost.org/ipw3945/daemon/ipw3945d-1.7.22.tgz
$ sudo tar xvfz ipw3945d-1.7.22.tgz
$ cd ipw3945d-1.7.22
$ sudo cp x86/ipw3945d /sbin

```

i've an error:
```
qaz@blue:/usr/src/ipw3945-1.1.0$ sudo ./unload
./unload: 2: Syntax error: "(" unexpected

```

---

### Post by n0dl on 2007-01-12
I remember reading in an article (as well as doing this when I ran 6.10) to simply get the restricted kernel modules. After that you just have to run the daemon it comes with and simply set the essid with
iwconfig essid eth? whateveryourconnectionnameis. 
After that run a dhclient on the device and retrieve an ip

---

### Post by uterrorista on 2007-01-13
i installed non-alternative version of ubuntu and, surprise, Wireless detected and installed.
:) :) :)
thanks :KS n0dl :KS

---

