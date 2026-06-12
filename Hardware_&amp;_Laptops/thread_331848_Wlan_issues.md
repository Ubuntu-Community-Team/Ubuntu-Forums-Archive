---
title: "Wlan issues"
date: 2007-01-05
forum: Hardware &amp; Laptops
---

### Post by drascus on 2007-01-05
I am having an issue with my wireless card it does not have a supported driver in Ubuntu. I found one via the web and it seems to be the correct one for my card, based on the native windows driver. I installed it via the Ndiswrappers GUI. it said the hardware was recognized and I moved to configure the card. But I never got a signal response from the card and the blue inicator light never turned on so I am wondering if the driver actually took. I don't know if I need to do the command as a root user to actually have it work properly (I don't know how to log in as root).  the type of computer I am using is a Compaq Presario V2000 the wireless card is a broadcom 802.11b/g air force one WLAN. I am running Ubuntu 6.06LTS. Please let me know if you guys need additional info. Any help would be greatly appreciated. 
~Mike~

---

### Post by eggdeng on 2007-01-05
```
ndiswrapper -l
``` will give you a list of installed drivers. You can execute commands as root by prefixing sudo to the command. If you really need to log in as root, boot in recovery mode to get a root terminal. if you assign a password to root ```
sudo passwd root
``` you will be able to log in as root in graphical mode. A better idea might be to have a look at [http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper) and make sure you have followed all the steps.

---

