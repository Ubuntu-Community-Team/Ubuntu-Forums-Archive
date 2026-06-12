---
title: "apt pinning"
date: 2009-06-15
forum: Installation &amp; Upgrades
---

### Post by jeremeym on 2009-06-15
I am trying to prevent certain packages from ever being updated (or installed as a dependency) with apt.

Could someone link to some documentation to help with this?

Thank you.

```
# cat /etc/apt/preferences 
Package: libkrb53
Pin: release *
Pin-Priority: -1


``````

# apt-cache policy | tail -5
 500 http://us.archive.ubuntu.com hardy/main Packages
     release v=8.04,o=Ubuntu,a=hardy,l=Ubuntu,c=main
     origin us.archive.ubuntu.com
Pinned packages:
     libkrb53 -> 1.6.dfsg.3~beta1-2ubuntu1.1

``````

# echo n | apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-image-server linux-server ntfs-3g
The following packages will be upgraded:
  apt imagemagick libcupsys2 libkrb53 libmagick10 libssl0.9.8 libtheora0 linux-image-2.6.24-23-server
  linux-ubuntu-modules-2.6.24-23-server sysv-rc tasksel-data
11 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 33.7MB/35.3MB of archives.
After this operation, 307kB of additional disk space will be used.
Do you want to continue [Y/n]? Abort.

```[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)
[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html)

---

