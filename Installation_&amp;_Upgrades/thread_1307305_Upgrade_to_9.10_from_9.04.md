---
title: "Upgrade to 9.10 from 9.04"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by nmyrick on 2009-10-31
I'm having difficulty upgrading from 9.04 to 9.10.  What happened was that I was in the middle of the upgrade when I lost my internet connection.  Now I am no longer getting an option to upgrade in the update manager.

I also cannot find the download for the "alternate CD," other than in a bit torrent, which I can't use because I live on the campus of a school where bit torrents are completely blocked on the network.

Can anyone tell me where I can get this "alternate CD"?   I really do not
want to do a complete reinstall.

Thanks,
nmyrick

---

### Post by morphodone on 2009-10-31
[http://www.ubuntu.com/getubuntu/downloadmirrors#mirrors](http://www.ubuntu.com/getubuntu/downloadmirrors#mirrors)

You should be able to restart the upgrade process though.

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

If you see karmic listed on the screen you will be fine.

---

### Post by nmyrick on 2009-10-31
I tried sudo apt-get upgrade, and all I get is the following.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Thanks,
nmyrick:popcorn:

---

### Post by macogw on 2009-10-31
It downloads before installing the packages for the upgrade.  Maybe you got disconnected after it finished downloading and you're done?

---

### Post by lindsay7 on 2009-10-31
Did you try pressing  the keys alt + f2, type update-manager -d  into the box.

---

### Post by nmyrick on 2009-10-31
Thank you Lindsay7, that worked!:p

---

