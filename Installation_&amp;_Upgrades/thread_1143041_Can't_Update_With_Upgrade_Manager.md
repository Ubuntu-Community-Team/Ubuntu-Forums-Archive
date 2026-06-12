---
title: "Can't Update With Upgrade Manager"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by Binary_Harmony on 2009-04-29
I've just upgraded to Jaunty and When ever I click install updates I get the Error  

```
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

```I just started to get this error since I updated to Jaunty.
 
Any suggestions on how to fix this??

---

### Post by Partyboi2 on 2009-04-29
Hi, make sure you only have one package manager running at a time eg synaptic, apt-get, update-manager, dpkg. If there are no package managers open then open a terminal (Applications>Accessories>Terminal) and check that there are no package manager processes running
```
ps -e
```look down the list and if you see any package managers running (synaptic, apt-get, update-manager, dpkg etc) kill the process with
```
sudo killall name
```
eg
```
sudo killall apt-get
```

---

