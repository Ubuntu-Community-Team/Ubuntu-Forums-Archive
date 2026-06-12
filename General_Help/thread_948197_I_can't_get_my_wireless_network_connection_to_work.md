---
title: "I can't get my wireless network connection to work"
date: 2008-10-15
forum: General Help
---

### Post by ladex142 on 2008-10-15
hi everyone, i can't seem to get the wireless network to work, the wireless signal is not even on, meaning that its not detecting any nearby network at all, its a hp pavilion dv7-1130us, here is the link to the wireless type on hp's website [http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-62508-1&lc=en&dlc=en&cc=us&lang=en&os=2100&product=3795407](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-62508-1&lc=en&dlc=en&cc=us&lang=en&os=2100&product=3795407) Please help.

---

### Post by pastalavista on 2008-10-15
Atheros wireless cards usually need [madwifi-tools]("http://packages.debian.org/unstable/net/madwifi-tools") available in Synaptic Package Manager or in the terminal
```
sudo apt-get install madwifi-tools
```

---

### Post by ladex142 on 2008-10-15
Thanks, am going to try it rightaway, but by the way, am having different ubuntu boot instances with am trying to boot into ubuntu, i thinks this is because i've install and uninstall ubuntu 2ice and it seems that it didn't uninstall completely or something, it looks something like this

windows vista
ubuntu
ubuntu
ubuntu

the first two is not working, then i'll have to click on the last one........how can i clean the first two, thanks.

---

### Post by ladex142 on 2008-10-15
from the terminal i got a result saying that E: Couldn't find madwifi-tools

from the synaptic package manager, i could even find a result that says madwifi, i got a result that says,
 
linux-restricted-modules-2.6.24-19-generic  
installed version 2.6.24.-19.44 
Description Non-free Linux 2.6.24 modules on x84/x86_64


how can i turn off the restricted modules

---

### Post by ladex142 on 2008-10-15
am tired of waiting, is anyone going to help

---

