---
title: "Installed server, skipped networking"
date: 2005-12-31
forum: Installation &amp; Upgrades
---

### Post by pfm102 on 2005-12-31
Hi

I just installed the server edition of ubuntu, but when I did it I hadn't wired in my ethernet, so I skipped that part of the install.  Now that it's installed, how do I go about setting up networking?  All the docs I've seen assume people have X installed, which I don't, and would like to avoid.

Also, can someone point me at docs describing how to set up LVM _and_ software RAID, preferably during the ubuntu installation?  I think I was too stupid to figure it out from the prompts the installer gives :(  I'm kind of after a best practise description of how to partition/setup LVM/setup RAID.

Cheers
Pete

---

### Post by Lambert on 2005-12-31
Open up this file

```
sudo vi /etc/network/interfaces
```

add lines like this for a static ip

auto eth0
 iface eth0 inet static
    address 192.168.0.42
    network 192.168.0.0
    netmask 255.255.255.0
    broadcast 192.168.0.255
    gateway 192.168.0.1

for dhcp add a line like this

auto eth0
  iface eth0 inet dhcp


then save the file and to bring up internet run this command

```
sudo ifconfig eth0 up
```

more information can be found in man pages

man interfaces
man ifconfig

---

