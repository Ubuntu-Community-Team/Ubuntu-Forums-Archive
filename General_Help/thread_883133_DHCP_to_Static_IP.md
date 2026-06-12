---
title: "DHCP to Static IP?"
date: 2008-08-07
forum: General Help
---

### Post by RATM_Owns on 2008-08-07
I know that you gedit /etc/network/interfaces and change the dchp thing to static and then have the address and such under it. 

But me, being the idiotic person that I am, doesn't know how to get those values.

If it matters, I'm using OpenDNS.

---

### Post by unutbu on 2008-08-07
Edit the wireless interface stanza /etc/network/interfaces to be something like this:
```
auto wlan0
iface wlan0 inet static
address 192.168.1.46     # Your static address
netmask 255.255.255.0
gateway 192.168.1.1      # Your router address

```

If you use WEP:```

wireless-key PUT-KEY-HERE
wireless-essid PUT-ESSID-HERE
```

If you use WPA, you'll find the right strings here:
[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

Change wlan0 to eth0 or whatever interface you wish to be made static.

---

