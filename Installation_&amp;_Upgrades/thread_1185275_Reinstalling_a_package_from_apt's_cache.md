---
title: "Reinstalling a package from apt's cache"
date: 2009-06-12
forum: Installation &amp; Upgrades
---

### Post by jim_p on 2009-06-12
Hello everyone.

Some months ago, in order to help a friend with her connection online, and prevent network manager from doing what it feels proper, I issued the removal of network manager and gnome-network-admin took its place.

For all these months everything worked out well, until she decided to switch to mobile internet and she was given a 
```
Bus 001 Device 003: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
```
from her ISP to do this connection.

I have found a tutorial on how to make this work, but it has one major difference from her setup, network manager :(
She has NO internet connection at all so as to reinstall it somehow, or install any similar app (some sites suggest wvdial).

So here lies my question. Can she grab network manager from apt's cache somehow?
And what about the dependencies? I don't think she has ever cleaned that cache.

Info:
Ubuntu 8.04, so it's network manager 0.6.x.
In dpkg -l, network manager appears as installed, it's line starts with "ii" (= is installed). However, doing a
```
sudo /etc/init.d/network-manager start
```
returns "Command not found".

Thank you in advance.

---

### Post by Kevbert on 2009-06-12
Have you tried re-installing using Synaptic Package Manager? The packages you need are network-manager and network-manager-gnome.
As an alternative you could download the files to a USB stick from [[COLOR="Red"]here[/COLOR]]("http://packages.ubuntu.com/jaunty/net/") (just replace jaunty in the link with her version of Ubuntu). The files will be .deb so just double-click on them to install.

---

### Post by jim_p on 2009-06-12
As I have said above 

She has NO internet connection at all so as to reinstall it somehow...

Plus, I think that network manager depends on more than the network-manager-gnome package as shown below, so even downloading the 2 .deb files, transfering them to the laptop and installing them with gdebi is a bit optimistic.

[http://packages.ubuntu.com/hardy/network-manager](http://packages.ubuntu.com/hardy/network-manager)

---

