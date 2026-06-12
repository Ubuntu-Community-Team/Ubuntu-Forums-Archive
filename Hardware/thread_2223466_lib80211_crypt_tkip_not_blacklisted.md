---
title: "lib80211_crypt_tkip not blacklisted"
date: 2014-05-11
forum: Hardware
---

### Post by keratos2 on 2014-05-11
need to remove tkip encyption and force AES (ccmp) , the latter is working however I cannot get rig of TKIP at boot time (although I can **rmmod** it) 
so I have updated /etc/modprobe.d/blacklist.conf and also created a new file /etc/modprobe.d/blacklist-80211.conf to add the line **blacklist lib80211_crypt_tkip **
and then run [B]depmod -a

[/B]rebooted - not blacklisted - still appears in **lsmod**

?

---

