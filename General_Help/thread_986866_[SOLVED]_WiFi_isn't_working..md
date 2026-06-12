---
title: "[SOLVED] WiFi isn't working."
date: 2008-11-19
forum: General Help
---

### Post by Newuser1111 on 2008-11-19
The WiFi isn't working in kubuntu on my Compaq Presario F756NR.

The WiFi is a "Atheros AR5007 802.11b/g WiFi Adapter".

---

### Post by Newuser1111 on 2008-11-19
Bump.

I do have Internet on it using Ethernet but I want WiFi.

---

### Post by Newuser1111 on 2008-11-21
Bump.

Why isn't anyone helping?
I've tried searching and nothing I found worked.

---

### Post by roger_1960 on 2008-11-21
Hi

I may or may not be able to help (I have a laptop with the same wifi).  You need to give more info:

Which version of ubuntu?
What have you already tried?

---

### Post by Crafty Kisses on 2008-11-21
First you need to make sure you have this package installed:
```
sudo apt-get install build-essential
```
Once you have that package installed, you need to fetch the driver, you can do that by doing the following:
```
wget http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz
```
Once you've done that it should start fetching the drivers and what not, once you have it, compile the driver and you should be set. For more information, I'd suggest you looking at this thread > [http://ubuntuforums.org/showthread.php?t=789824&page=2](http://ubuntuforums.org/showthread.php?t=789824&page=2)

---

### Post by bodhi.zazen on 2008-11-21
[http://my.opera.com/williamn/blog/2008/08/30/enabling-atheros-ar5007-based-wireless-on-ubuntu-8-04](http://my.opera.com/williamn/blog/2008/08/30/enabling-atheros-ar5007-based-wireless-on-ubuntu-8-04)

---

### Post by Newuser1111 on 2008-11-21
> **roger_1960 said:**
> Hi

I may or may not be able to help (I have a laptop with the same wifi).  You need to give more info:

Which version of ubuntu?
What have you already tried?Kubuntu 8.10.
Some file that worked on Ubuntu 8.04 and some things I found by searching the forums.

> **bodhi.zazen said:**
> [http://my.opera.com/williamn/blog/2008/08/30/enabling-atheros-ar5007-based-wireless-on-ubuntu-8-04](http://my.opera.com/williamn/blog/2008/08/30/enabling-atheros-ar5007-based-wireless-on-ubuntu-8-04)```
djk@djk-laptop:~/WiFi$ wget http://snapshots.madwifi.org/special/madwifi-hal-0.10.5.6-r3698-20080604.tar.gz
--2008-11-21 17:37:32--  http://snapshots.madwifi.org/special/madwifi-hal-0.10.5.6-r3698-20080604.tar.gz
Resolving snapshots.madwifi.org... 217.24.1.134
Connecting to snapshots.madwifi.org|217.24.1.134|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://snapshots.madwifi-project.orgspecial/madwifi-hal-0.10.5.6-r3698-20080604.tar.gz [following]
--2008-11-21 17:37:33--  http://snapshots.madwifi-project.orgspecial/madwifi-hal-0.10.5.6-r3698-20080604.tar.gz
Resolving snapshots.madwifi-project.orgspecial... failed: Name or service not known.
wget: unable to resolve host address `snapshots.madwifi-project.orgspecial'

```

> **Codename said:**
> First you need to make sure you have this package installed:
```
sudo apt-get install build-essential
```
Once you have that package installed, you need to fetch the driver, you can do that by doing the following:
```
wget http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz
```
Once you've done that it should start fetching the drivers and what not, once you have it, compile the driver and you should be set. For more information, I'd suggest you looking at this thread > [http://ubuntuforums.org/showthread.php?t=789824&page=2](http://ubuntuforums.org/showthread.php?t=789824&page=2)
Done that before, worked on Ubuntu 8.04 but didn't work in Kubuntu 8.10

---

### Post by Newuser1111 on 2008-11-22
It still isn't working.

I'll try this in a hour:
[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

EDIT:
It worked!! :D

---

