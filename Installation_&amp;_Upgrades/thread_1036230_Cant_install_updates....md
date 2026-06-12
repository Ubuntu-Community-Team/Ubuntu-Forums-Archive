---
title: "Cant install updates..."
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by 00101 on 2009-01-10
Ok, im new to ubuntu and linux in general, and have quite a few problems.
1) this is the most major problem i have, I CANT INSTALL ANYUPDATES OR SOFTWARE! everytime i try to it just throws up this error "E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

2)because of problem 1 i cant get my wireless internet card to work. it recongizes that its there and that it has the drivers installed but it wont detect any networks and i did try to enter all the data manually, but it just instantaneously disconnected after i hit ok. my wireless card model is a "Dynex DX-EBDTC"

3)anything else that wont work without updates

---

### Post by Partyboi2 on 2009-01-10
> 1) this is the most major problem i have, I CANT INSTALL ANYUPDATES OR SOFTWARE! everytime i try to it just throws up this error "E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory Make sure you only have one package manager open at a time eg. add/remove, synaptic package manager, apt-get

---

### Post by avtolle on 2009-01-10
The error message you have set out in problem 1 generally means there is another package manager open. Check to see if you have inadvertently left Synaptic open, or if Update Manager is already open, whatever. If so, close the offending package, and wait until the gray icon leaves the top panel, and try it again.

---

### Post by 00101 on 2009-01-10
Ok, unless there is one running in the backround, i only have one open.

---

### Post by Partyboi2 on 2009-01-10
Open a terminal (Applications>Accessories>Terminal) and type
```
ps -e
``` look at the current processes and check that there is no 
package manager running eg synaptic, update-manager
if there is then use
```
killall ?
```replace ? with name of package manager
eg.
```
killall synaptic
```If there is none then you can try to remove the lock file
```
sudo rm var/cache/apt/archives/lock
```

---

### Post by 00101 on 2009-01-14
Ok, i got the updates installed ill put in another reply if i still cant get the wireless working and thanks to everyone for the help

---

