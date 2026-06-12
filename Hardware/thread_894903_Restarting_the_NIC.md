---
title: "Restarting the NIC?"
date: 2008-08-19
forum: Hardware
---

### Post by jpeery on 2008-08-19
Often, my Linksys router gets locked up when running torrents.  When this happens I have to restart the router, but then my PC (laptop) doesn't ever "reconnect" unless I restart.  Is there a certain command I could run that would restart the NIC?
Thanks!
JP

---

### Post by caljohnsmith on 2008-08-19
Usually all you need to do is:
```
sudo ifdown <interface>
sudo ifup <interface>
```
Where <interface> is wlan0, eth1, or whatever yours is. If ifdown and ifup don't do the trick, sometimes it is helpful to restart networking:
```
sudo /etc/init.d/networking restart
```

---

### Post by jpeery on 2008-08-19
Will give that a try, thanks!
JP

---

