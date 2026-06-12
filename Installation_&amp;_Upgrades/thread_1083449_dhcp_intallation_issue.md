---
title: "dhcp intallation issue"
date: 2009-03-01
forum: Installation &amp; Upgrades
---

### Post by robasc on 2009-03-01
I am trying to install dhcp on my pc. I am currently using ubuntu 8.10.

Here is my error message:

root@master-node:/etc# sudo apt-get install dhcp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package dhcp is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package dhcp has no installation candidate
root@master-node:/etc# 


any help would be appreciated!!!

---

### Post by taurus on 2009-03-01
Do you want the client or the server?

```
sudo apt-get update
sudo apt-get install dhcp3-client
```

---

### Post by robasc on 2009-03-01
I see, I must specify client or server. Thanks!

---

