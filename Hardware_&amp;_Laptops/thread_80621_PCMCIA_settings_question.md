---
title: "PCMCIA settings question"
date: 2005-10-22
forum: Hardware &amp; Laptops
---

### Post by Zymous on 2005-10-22
The only way that I can get my PCMCIA slot to work with my wireless card (Toshiba Equium A60 and a Linksys WPC11 ver 4 card) is to run the command

setpci -s 0:14.4 SUBORDINATE_BUS=03

I've moved this to  the /etc/init.d/bootmisc.sh script, but this still runs after the network detection and I need to insert the card after this and then run another script to bring the network.

Is there any way of running this command (or someting similar) earlier in the boot sequence so that the card can be detected and the network brought up automatically?

Thanks in advance.

-- 
Zym

Postscript.
To activate the PCMCIA card and bring up the network I run this script /root/setpci.sh


```
cardctl eject
setpci -s 0:14.4 SUBORDINATE_BUS=03
cardctl insert

iwconfig wlan0 key restricted s:{password}
iwconfig wlan0 essid {ESSID}
dhclient wlan0
```


by doing this


```
sudo -s
[enter password]
crontab -e -u root
```


and adding this line 

```
@reboot /root/setpci.sh

```

to the file.

---

### Post by spiregrain on 2005-12-23
I had the same problem, and added the set_pci line to the start of the "start" section of /etc/init.d/pcmcia, and then added a "cardctl eject" and "cardctl insert" before the end of the start section.

Works for me, but there must be a better place for it...

---

