---
title: "Recent problem showing up"
date: 2009-03-06
forum: Installation &amp; Upgrades
---

### Post by Sojurner on 2009-03-06
The last few times ive tried to install something and even do the updates ive been getting this error message. 

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

---

### Post by Partyboi2 on 2009-03-06
Make sure you only have one package manager open at a time. eg synaptic, update manager, apt-get..... If you have more then one in use you will get that message.

---

### Post by Sojurner on 2009-03-06
as far as i know i do. any other reason why i would get that messege?

---

### Post by Partyboi2 on 2009-03-06
If you open a terminal  and check the running processes to see if there is no package manager running.
```
ps -e
``` If there is then you can use
```
killall process name
``` change process name to actually name. eg ```
killall synaptic
```
If you are sure still that there is no package manager running then you can try removing the lock file.
```
sudo rm /var/cache/apt/archives/lock
```

---

