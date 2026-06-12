---
title: "can see wireless networks, but can't connect"
date: 2010-05-05
forum: Hardware
---

### Post by CarNut1981 on 2010-05-05
Hi

I am dual running XP home and ubuntu 10.04 the only thing stopping me from doing away with windows is the WIFI issue. I can see the networks but it will not connect, I am using an old Satellite pro 4600. I have heard that it my be an issue with the orinoco driver or a frequency issue, plz help thanks

*note: I am relitively new to ubuntu though I have run older version's on another mechine with no issues. will try to post iwconfig readout later if needed

---

### Post by Detonate on 2010-05-05
Try this.
```
sudo apt-get install wicd
```
```
sudo apt-get remove network-manager network-manager-gnome
```

---

### Post by CarNut1981 on 2010-05-17
thanks it worked like a charm on it right now

---

